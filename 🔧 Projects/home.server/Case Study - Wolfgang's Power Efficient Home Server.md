# Case Study
[Wolfgang's Power Efficient Home Server](https://www.youtube.com/watch?v=MucGkPUMjNo&list=WL&index=41)

### Recommendations
- **Don't buy old hardware**
- **Newer doesn't necessarily mean more power efficient**

### Build
**CPU**
- Power saving is not as easy as buying a low TDP CPU and pairing with a motherboard
- 6th or 7th Intel CPU will be fairly power efficient and budget friendly
- Intel tends to win on power efficiency vs AMD 
- TDP means nothing for the real world power consumption of a home server as it only describes power consumption under load, so avoid T-Series Intel chips as they are more expensive with no real benefits.
- Things to look for: *Idle system power consumption*, *PassMark score*

**Motherboards**
It is important that the motherboard is optimized for power efficiency. Multiple onboard devices can add up to 10-15 Watts to power draw.
- **Mini ITX:** Less ports and features compared to regular ATX counterparts, but are power efficient. Some good options are:
	- Fujitsu D3417-B11 (4W)
	- Gigabyte C246N-Wu2 (5.07W)
	- MSI Z1701 Gaming Pro AC (5.3W)
	- ASRock H510M-HVS R2.0 (5.4W)
	- ASRock H410M-HDV R2.0 (5.4W)
	- ASRock B85M-ITX (5.7W)
	- Asus H110i-Plus (6W)
- **mATX and ATX:** Recommendation is to find motherboards that support at least Intel 8th gen CPUs. Some options:
	- Fujitsu 8th and 9th gen
	- Fujitsu 6th and 7th (won't work with Intel 8th gen)

**Package C-States**
Power efficient semi-idle states the system can go in to if not a whole lot is going on. The higher number on the C-state cooresponds to higher power savings.