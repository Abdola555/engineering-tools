# Transformer Core, Bobbin & Ferrite Material Database

**Version:** 1.0  
**Status:** Active  
**Type:** Offline Excel workbook (`.xlsx`) — no installation, no internet required

## What it is

A single workbook holding the core geometry, coil former, ferrite material and
magnet wire data needed to size an SMPS transformer or inductor — plus two live
calculator sheets that turn that data into a starting design.

Every data row is built from the manufacturer's own datasheet or catalogue, and
carries a link to the exact document it came from (sheet `11_Sources`).

**Scope:** soft-ferrite (MnZn / NiZn) cores, coil formers and materials for
switch-mode supplies. Powder cores, nanocrystalline / amorphous tape cores and
50/60 Hz silicon-steel laminations are **not** covered.

## Sheets

| Sheet | Contents |
|-------|----------|
| `00_README` | Scope, symbol definitions, how-to-use walkthrough, caveats |
| `01_Materials_Global` | 50+ ferrite grades — TDK Japan (PC/PE), TDK Electronics/EPCOS (SIFERRIT N), Ferroxcube, Magnetics Inc, Fair-Rite |
| `02_Materials_China` | Chinese grades — DMEGC (Hengdian), TDG Holding (Acme), New Conda |
| `03_Material_XRef` | Advisory cross-reference between vendors, grouped by material class, with basis and confidence columns |
| `04_Cores_All` | 80+ core geometries in one filterable table — ETD, E/EF, EE/EI/EER, EFD, PQ, RM/EP/ER, planar ELP/EILP, toroid |
| `05_Bobbins` | Coil formers matched to each core: pins, winding window AN, mean length of turn lN, AR, plastic |
| `06_Bobbin_Materials` | Coil former plastics with UL file numbers, UL 94 rating and insulation class |
| `07_Gapped_AL` | Published AL / air-gap combinations — starting points for flyback and inductor designs |
| `08_AWG_Wire` | AWG table: bare diameter, area, R at 20 °C and 100 °C, grade 1 / grade 2 build, matching Furukawa TEX-E (TIW) size |
| `09_Design_Calculator` | Live sizing calculator with a core drop-down. Yellow cells are inputs/overrides, green is the value actually used |
| `10_Winding_Window` | Up to five windings: wire sizing from current density, skin-depth limit, strand count, window-fill check against Aw |
| `11_Sources` | Every source document used, with publisher, URL and what was taken from it |

## How to use it as a starting design

1. Enter your converter data on `09_Design_Calculator`. It returns the target
   area product Ap — you can override that target and carry on from your own number.
2. Pick a core from the drop-down, or filter the Ap column on `04_Cores_All`
   for the first core that exceeds the target. Prefer ETD/PQ for wound
   transformers, planar ELP for PCB windings.
3. Choose the material on `01_Materials_Global` / `02_Materials_China` by
   switching frequency and expected core temperature, then select that grade in
   the material drop-down so AL is looked up for you.
4. Read the turns off section 3 and check peak flux at **Amin** against
   0.6 × Bs(100 °C).
5. Go to `10_Winding_Window`. Enter turns and RMS current per winding, pick an
   AWG at or below the skin-depth limit, set the strand count until the copper
   check passes, choose enamel or TIW — then read the window fill ratio and verdict.

## Caveats

- **Test conditions differ.** Bs is quoted at 1200 A/m by TDK/EPCOS/Ferroxcube,
  at 15 Oe (~1194 A/m) by Magnetics, and at 5 Oe (~398 A/m) by Fair-Rite —
  Fair-Rite numbers are *not* directly comparable.
- **Pv test points differ.** TDK Japan quotes core loss at 25 °C, TDK Europe /
  EPCOS at 100 °C. Read the "Pv test condition" column before comparing grades.
- **Geometry is standardised, AL is not.** ETD/E/EFD/PQ/RM/EP/planar shapes
  follow IEC 63093 / 62317, so Ae, le, Ve are essentially identical across
  vendors for the same size. AL follows the material.
- **The cross-reference is advisory.** Sheet `03` matches grades by published
  properties; it is not a manufacturer-endorsed equivalence. Re-qualify a second
  source on your own hardware.

## Opens in

Microsoft Excel 2016+, LibreOffice Calc 7+, Google Sheets (drop-downs and
lookups on the calculator sheets are best in Excel).

## Sources

Sheet `11_Sources` lists all 40+ source documents: TDK Corporation (Japan),
TDK Electronics / EPCOS, Ferroxcube, Magnetics Inc (Spang), Fair-Rite Products,
DMEGC / Hengdian Group, TDG Holding (Acme), New Conda, Elektrisola,
MWS Wire Industries and Furukawa Electric. Sizing method on sheet `09` follows
Wm. T. McLyman's area-product approach.
