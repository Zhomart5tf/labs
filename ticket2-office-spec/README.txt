# Ticket 2: Office spec (second office)

## 1. Request and the director's assumption
Daniyar K. (Director) asks for computers for the second office: an accountant, a sales manager, a web developer and a designer. The budget is 3,000,000 KZT for everything, monitors included. He assumes we should buy the same machine for everyone. That assumption is wrong: the four roles have different workloads, so an identical machine would be wasted on one role and too weak for another. This report therefore specifies four different machines.

## 2. Four builds
The full description of each machine (load, bottleneck, trade-off) is in [builds.md](builds.md). Every machine has at least 16 GB of RAM, a 1 TB SSD, a licensed Windows 11 and a monitor.

| Role | CPU | RAM | Graphics | Monitor | Bottleneck | Total, KZT |
|---|---|---|---|---|---|---|
| Accountant | Intel Core i3 12100 | 16 GB | integrated | iiyama 24" | SSD speed, memory | 476,440 |
| Sales manager | AMD Ryzen 5 7500F | 32 GB | integrated | Xiaomi G27Qi 27" | memory | 569,530 |
| Web developer | AMD Ryzen 7 9700X | 32 GB | integrated | MSI MAG 275QF 27" | memory, CPU cores | 808,340 |
| Designer | AMD Ryzen 7 9700X | 32 GB | RTX 4060 Ti 8 GB | MSI MAG 275QF 27" | GPU, memory, monitor | 1,058,930 |

## 3. Budget
Total: 2,913,240 KZT out of 3,000,000 KZT, so the budget is respected with 86,760 KZT left. All prices, sources and dates are in [budget.csv](budget.csv). Prices were taken on 15.11.2026 from shop.kz, which delivers to Kazakhstan.

## 4. Answers to the three questions

**1. Which of the four machines will I upgrade first, eighteen months from now, and why?**
The web developer's machine: memory from 32 GB to 64 GB. Docker containers and virtual machines need more RAM every year, and a RAM upgrade is cheap and quick, while the CPU and SSD are still adequate after eighteen months.

**2. Price the same four as pre-built machines from a vendor. What does the company gain and what does it lose by not building them?**
The four pre-built machines cost <prebuilt total> KZT (shop.kz, 15.11.2026); see `evidence/vendor-quotes/prebuilt-quote.png`. The company gains: ready-made machines, one warranty, no time spent assembling and testing. The company loses: tuning to each role (the money does not go where the bottleneck is, for example memory for sales or the GPU for the designer), it pays more for the same performance, and pre-built machines may use non-standard parts that limit later upgrades.

**3. Which of these four people will complain about performance within a month, and about what?**
The designer. Large PSD files and Figma depend on the graphics card and memory. Because of the budget the graphics card is mid-range (RTX 4060 Ti), so heavy files with many layers will lag during filters and export.

## 5. Evidence
- [evidence/pcpartpicker-links.md](evidence/pcpartpicker-links.md)
- evidence/vendor-quotes/ (screenshots of prices with the date visible)