# Lab 5 — Encoding forensics

## Diagnosis (before the fix)
file says: Non-ISO extended-ASCII text, with CRLF line terminators (from evidence/file-before.txt)

First 16 bytes (from evidence/hexdump-before.txt, with the table):

| Offset | Bytes | What they are |
|---|---|---|
| 00-02 | D2 E0 E1 | No BOM (not EF BB BF); already the first characters of the header, single-byte Cyrillic letters |
| 03-04 | 2E B9 | "." and the "№" sign, one byte each |
| 05 | 3B | Separator: semicolon |
| 06-08 | D4 C8 CE | Next column header, single-byte Cyrillic letters |
| 09 | 3B | Separator: semicolon |
| 0A-0F | C4 EE EB E6 ED EE | Next column header, single-byte Cyrillic letters |
| 00 | D2 | The first non-ASCII character takes 1 byte (no D0/D1 pairs), so it is not UTF-8 |

The line ending is not in the first 16 bytes; it is proven by the CR and LF counts below.

Encoding: RK1048 — evidence: the UTF-8 check failed with "iconv: illegal input sequence at position 0"; every byte above 7F is a single byte, so it is a single-byte code page; decoded with RK1048 the whole file gives "ok" and all names, including the Kazakh letters, read correctly.
Line ending: CRLF — evidence: file says "with CRLF line terminators"; CR count = 26, LF count = 26, they are equal.
BOM: absent — evidence: the file starts with D2 E0 E1, not EF BB BF.
SHA-256 of the original staff-broken.csv: 919027f1f8c71d85cba3f12aad0f6c927d4e0450cfb2a2d63378a69f14cab270

## What each application was doing wrong
Excel: assumed the system ANSI code page, not UTF-8, because the file has no BOM, so the Kazakh letters were shown wrong.
LibreOffice: showed the Text Import dialog and proposed a character set by guessing from the bytes.
cat: sent the raw bytes to a UTF-8 terminal; single-byte letters are not valid UTF-8 there, so the names showed as noise.

## Fix
Command / script: scripts/fix.sh
Changed: encoding RK1048 -> UTF-8; line ending CRLF changed to LF (CR removed with sed);
BOM added, because Excel decided it: without a BOM it does not recognise UTF-8 on double-click.
The original evidence/staff-broken.csv is untouched: its SHA-256 after the fix is the same as above.

## Verification
file after: (from evidence/file-after.txt)
Opened in: Excel Microsoft 365, LibreOffice Calc 24.8, cat on Ubuntu Ubuntu 24.04 LTS
— evidence/opens-correctly.png
