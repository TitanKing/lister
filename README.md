# CWE3D Lister 3D Printer Documentation

## Introduction

The CWE3D Lister is a 3D printer engineered for reliability, precision, and ease of maintenance. While its design draws inspiration from various open-source projects, including [Voron Design](https://docs.vorondesign.com/), [Prusa Research](https://www.prusa3d.com/), and [RatRig](https://ratrig.com/), the Lister has evolved into a unique machine tailored for specific use cases.

## Printer Purpose and Design Philosophy

The Lister 3D printer is designed for:

- 3D Printing Enthusiasts
- Engineers
- Hobbyists
- Universities and Educational Institutions
- Industries with general 3D printing needs

Our design philosophy prioritizes:

1. Reliability
2. Maintainability
3. Simplicity (KISS principle)
4. Consistent, successful prints
5. Modifiability
6. Aesthetics
7. Precision
8. Durability
9. Open-source principles and community support

It's important to note that the Lister is not designed to compete with high-speed, performance-oriented, or fully enclosed machines like some Voron or RatRig models. Instead, it focuses on consistent, high-quality prints with a range of common and engineering-grade filaments that don't require special environmental controls.

## Filament Compatibility

The Lister 3D printer is optimized for filaments that:
- Don't require a heated chamber
- Are less prone to warping
- Don't need bed temperatures exceeding 90°C

Compatible filaments include:

1. PLA variants (Standard, PLA+, filled PLAs, specialty PLAs)
2. PETG and its variants (including CF and GF reinforced)
3. TPU/TPE (up to 95A hardness)
4. PVA (for soluble supports)
5. PCTG
6. Some low-warp nylon blends
7. Various specialty and bio-based filaments

The printer itself uses:
- eSun ePLA-ST for most parts
- eSun PETG for black back panels
- Bamboo Labs PEGT-CF for brackets
- eSun TPU 95A for anti-vibration feet

### 0.6mm Hardened Nozzle

The Lister uses a 0.6mm hardened steel nozzle, chosen for:
- Improved flow with engineering filaments like PETG-CF
- Capability for 0.3mm layer heights, balancing strength and print speed
- Resistance to abrasive filaments
- Reduced backpressure compared to 0.4mm nozzles

This choice reflects our focus on practical, reliable printing rather than ultra-fine detail work.

## Key Features

### Reliability

### Precision

#### Bed Flatness 

### Simplicity

## Just received your printer?

Thank you for supporting us. We hope that this investment was a valuable purchase in your life. The Lister is designed to exceed required specifications in many areas, helping it to last as long as possible.

Each printer undergoes hours and days of tuning, with every single part quality checked to a measured level. While transit can be tough, we continually work to perfect our packaging.

### Unboxing

1. Carefully unscrew the entire wooden protective structure surrounding the printer before attempting to lift it out. This precaution prevents damage to small components like the runout sensor and stops the gantry from catching on the top box storage structure.
2. Once the printer is free from its packaging, place it on a sturdy, level surface capable of supporting its weight.

### Inspection

1. Examine the XY gantry for any obstructions. Gently move the gantry using the designated handle, ensuring it moves freely and smoothly along both axes.
2. Conduct a thorough visual inspection for any obvious damage:
   - Check all corners and edges for signs of impact or breakage
   - Verify that all belts are correctly seated on their respective idler pulleys
   - Look for any other signs of damage or misalignment
3. Ensure the power cable running to the heated bed is not trapped behind a leg or obstructed in any way.
4. If you discover any damage that appears to have occurred during shipping, please contact our support team immediately for assistance.

## Powering Up Your Printer

It's time to power up your Lister 3D printer. The main power switch is located where the power cord enters the machine.

### Main 220V Switch Powers:

- The Raspberry Pi (always-on microcomputer)
- All other printer components

<span style="color: orange">**Important:**</span> Never abruptly cut power using this switch. Doing so can interrupt the Raspberry Pi, potentially corrupting the Micro SD card. <span style="color: orange">**Always shut down properly via the Web Interface**</span> (detailed instructions provided later).

### Main Board 24V Switch

This switch powers the 24V Bigtreetech SKR Pro V1.2 control board.

## Establishing a Connection

Your Lister 3D printer runs on [RatOS](https://os.ratrig.com/docs/introduction/), a Linux-based operating system. RatOS broadcasts a Wi-Fi access point and can also accept wired network connections.

After powering on both the 220V and 24V switches, allow 1-2 minutes for the system to fully boot. You can then connect using one of two methods:

1. Wi-Fi Connection
2. Wired Ethernet Connection (faster and more reliable)

### Wi-Fi Connection

1. On your Wi-Fi-enabled device, look for a network named similar to:
   - printername.local (e.g., ionflux.local, cwe3d.local)
   - RatOS or ratos.local
2. Connect using the default password: **raspberry**
3. Open a web browser and navigate to the printer's local domain:
   - http://printername.local, http://RatOS.local, http://cwe3d.local, etc.
4. To set up your personal Wi-Fi network:
   - Browse to http://printername.local/configure
   - Find your Wi-Fi network and enter your password
   - On the next screen, you can customize the printer's domain name

### Wired Ethernet Connection

1. Connect an Ethernet cable between your printer and your network
2. Open a web browser and navigate to:
   - http://printername.local, http://RatOS.local, http://cwe3d.local, etc.
3. If you only used the Ethernet connection temporarily, you can follow the Wi-Fi setup steps to enable wireless connectivity.

After completing these steps, you'll have full access to your Lister 3D printer's web interface for monitoring and control.

## Bed Leveling

### Manual Bed Adjustment

Before starting your first print, it's crucial to ensure your print bed is properly leveled. The Lister 3D printer includes a helpful macro called `BED_PROBE_MANUAL_ADJUST` to assist you with this process.

#### Using BED_PROBE_MANUAL_ADJUST

1. In the Mainsail interface, locate the "MACROS" section in the main control panel.
2. Find and click on the `BED_PROBE_MANUAL_ADJUST` button.
3. The printer will begin the bed leveling process:
   - It will home all axes if they aren't already homed.
   - The probe will measure multiple points on the bed.
   - Mainsail will display the results in the main control panel.

#### Interpreting the Results

After the probing is complete, you'll see a visualization of the bed's tilt in the Mainsail interface. This will typically appear as a grid or a set of values corresponding to different points on the bed.

- The numbers represent the deviation from a perfectly flat bed in millimeters.
- Positive numbers indicate that the bed is too high at that point.
- Negative numbers indicate that the bed is too low at that point.

#### Adjusting the Bed

Based on the results:

1. Identify the corners that need adjustment.
2. Use the bed leveling screws located under the bed to make adjustments:
   - If a corner shows a positive number, turn the corresponding screw clockwise to lower that corner.
   - If a corner shows a negative number, turn the corresponding screw counterclockwise to raise that corner.
3. Make small adjustments (about 1/8 to 1/4 turn) at a time.
4. After adjusting, run the `BED_PROBE_MANUAL_ADJUST` macro again to check your progress.
5. Repeat the process until all points are as close to zero as possible (typically within ±0.05mm).

### Important Notes

- This manual adjustment is crucial for achieving optimal first layer adhesion and overall print quality.
- It's recommended to perform this adjustment periodically or after any significant changes to your printer setup.
- If you're having persistent issues with bed leveling, please consult the troubleshooting section of this manual or contact support.

By ensuring your bed is properly leveled using the `BED_PROBE_MANUAL_ADJUST` macro, you're setting a strong foundation for successful, high-quality prints with your Lister 3D printer.

## Conclusion

The CWE3D Lister 3D printer is engineered for users who prioritize reliability, ease of use, and consistent results over extreme speed or specialized high-temperature materials. It's ideal for educational settings, engineering prototyping, and hobbyists who need dependable performance with a wide range of standard and engineering filaments.

While it may not be suitable for all applications, particularly those requiring enclosed printing environments or extremely high-temperature materials, the Lister excels in its intended use cases. It offers a balance of quality, reliability, and versatility for the majority of 3D printing needs.

We encourage users to explore the capabilities of this printer and engage with our community for support, modifications, and shared experiences. The Lister is more than just a printer; it's a platform for creativity and engineering problem-solving.