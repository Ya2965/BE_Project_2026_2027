# NIR Spectroscopy Fundamentals

## Project context

Near-infrared (NIR) spectroscopy studies the interaction of near-infrared light with a material. In this project, NIR illumination at 850 nm and 940 nm is directed through a finger, and transmitted light is detected using a photodiode.

The measured signal depends on the optical properties of the tissue and the complete measurement arrangement. It can also be affected by geometry, placement, perfusion, temperature, and other physiological or environmental factors.

## Transmitted-light measurement

The BPW34 photodiode converts incident optical power into a current. A transimpedance amplifier converts this current into a voltage, which is then digitized by an ADC.

The project records OFF and LED-ON voltages and calculates wavelength-specific response values:

\[
\Delta_{850}=V_{\mathrm{OFF1}}-V_{850}
\]

\[
\Delta_{940}=V_{\mathrm{OFF2}}-V_{940}
\]

These values are electrical/optical response features from the prototype. They are not direct glucose concentration measurements.

## Beer–Lambert law

For an idealized homogeneous, non-scattering medium, the Beer–Lambert relationship is commonly written as:

\[
A=\log_{10}\left(\frac{I_0}{I}\right)=\epsilon c l
\]

where:

- \(A\) is absorbance
- \(I_0\) is incident intensity
- \(I\) is transmitted intensity
- \(\epsilon\) is the molar absorptivity
- \(c\) is concentration
- \(l\) is optical path length

Biological tissue is a complex, strongly scattering medium. Therefore, the simple Beer–Lambert expression is a conceptual starting point and should not be applied as a direct glucose-calculation equation for this finger-sensing prototype without an appropriate tissue-optics model and experimental validation.

## Interpretation in this project

The current prototype measures voltage changes associated with two NIR illumination channels. Establishing whether these features contain glucose-associated information requires:

- Reliable optical and electronic measurements
- Controlled and documented finger placement
- Reference glucose measurements
- Repeated observations
- Consideration of perfusion and other physiological factors
- Appropriate statistical analysis

## Important distinction

A measurable NIR response is evidence that the optical front end is operating. It is not, by itself, evidence of glucose sensitivity or clinical measurement accuracy.
