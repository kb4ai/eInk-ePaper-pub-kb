# Dasung Small E-ink Monitor Models - Technical Overview

## Model Specifications

### Paperlike 103 (10.3")
- **Display**: 10.3" E-ink, 1872×1404px, 4:3 AR, 227 PPI
- **Refresh**: 60Hz (world's fastest E-ink refresh)
- **Interface**: USB-C (video+power), capacitive touch
- **Features**: Color-adjustable frontlight, auto-ghosting removal
- **Power**: Likely requires external adapter due to 60Hz refresh (unconfirmed)
- **Price**: $349 USD (¥1,999 CNY domestic)
- **Trade-offs**: Potential ghosting artifacts at max refresh

### Paperlike 13K Revolutionary (13.3") - Monochrome
- **Display**: 13.3" E-ink, 3200×2400px (3K), 4:3 AR, 300 PPI
- **Refresh**: 37Hz with proprietary acceleration tech
- **Build**: 5mm thick aluminum chassis, 1.6 lbs (726g)
- **Interface**: USB-C + Mini-HDMI, DC power port, 3.5mm audio
- **Power**: External DC adapter required (included)
- **Variants**:
  - Base: $679 (no FL/touch)
  - FL only: $699
  - FL+Touch: $749 (Windows/Linux only)
- **Compatibility**: Windows, Linux, limited macOS

### Paperlike 13K Revolutionary Color (13.3")
- **Display**: 13.3" Kaleido 3, 3200×2400px native, 300 PPI mono/150 PPI color
- **Refresh**: 37Hz
- **Color**: 4096 colors, reduced resolution in color mode
- **Power**: External DC adapter required (included)
- **Features**: Frontlight + capacitive touch standard
- **Price**: $749 USD
- **Note**: Same chassis/interface as monochrome variant

### Paperlike HD Series (13.3") - Legacy
- **Display**: 13.3" E-ink, 2200×1650px, 207 PPI
- **Refresh**: Standard refresh (non-Revolutionary)
- **Interface**: USB-C + HDMI + 3.5mm
- **Power**: USB-powered (5V-2A), no external adapter needed
- **Price**: $699 (when available)
- **Status**: Superseded by 13K series

## Technical Notes

**Refresh Technology**: Dasung's proprietary controller achieves high refresh rates through partial refresh algorithms and aggressive ghosting compensation. Trade-off between refresh speed and image persistence.

**Kaleido 3**: Color filter array over monochrome E-ink. Effective resolution halved in color mode due to RGBW subpixel arrangement.

**Power Requirements**:
- **Revolutionary series (33Hz+)**: Require external DC adapter, exceed USB power limits
- **HD series**: USB-powered (5V-2A, ~10W max), suitable for mobile use
- **Pattern**: High refresh rates (>30Hz) = external power required
- See detailed analysis: `Dasung-Paperlike-External-Power-Requirements-mobile-vs-power-adapter-models.md`

**Latency**: Sub-30ms input lag on 37Hz+ models. Touch adds 5-10ms.

**OS Support**: Full Windows/Linux. macOS limited to display mirroring, no extended desktop.