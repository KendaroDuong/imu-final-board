# Psionic IMU: Final Board (Rev-02)

KiCad project for the final board of the Psionic prototype IMU (VT ECE 4805, Team S27-49).
Rev-01, the 60 mm x 60 mm breakout board, is in [imu-breakout-board](https://github.com/KendaroDuong/imu-breakout-board).

## Status
| Item | State |
|---|---|
| Sensor sheets (`Accel_Gyro`, `Mag_Baro`) | Carried over from Rev-01, `origin/adrian` commit `44ecbd0` |
| MCU sheet | Drawn: STM32F411CEU6, crystal, decoupling, reset and boot straps, status LED |
| Power, M.2 and I/O sheet | Drawn: M.2 Key B connector, 3.3 V input filter, USB, UART and trigger protection, test pads |
| PCB | M.2 2260 Key B outline with a 4-layer, 0.8 mm stackup; other parts not imported yet |

ERC reports 5 warnings and errors, all from the Rev-01 sensor sheets. They are false alarms from the sensors' internal-regulator pins (U1 `V1P8`, U4 `CAP`) and pins with an unspecified type on the ADXL380 symbol.

The schematic has not been reviewed by a person yet. Part values for the crystal load capacitors, ferrite beads and ESD parts need checking against the parts you buy.

To bring the parts into the PCB, open it and run Update PCB from Schematic with **Re-link footprints to schematic symbols based on their reference designators** turned on, so the existing M.2 outline (`J1`) links to its symbol.

## Layout
- `Final_Board/`: KiCad 10 project. Open `Final_Board.kicad_pro`.
- `Final_Board/Libraries/`: symbols and footprints for the four sensors.
- `docs/`: hardware design document with the Rev-01 to Rev-02 changes.

## Next steps
1. Confirm the M.2 key and the UART and trigger pin choices with Psionic.
2. Review the schematic with the team and mentor.
3. Run Update PCB from Schematic, then place and route.
4. Design the bench carrier board.
