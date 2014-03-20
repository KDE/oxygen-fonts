# Oxygen Font

Oxygen Font is a project to design a desktop/gui font for integrated
use with the KDE desktop.

The basic concept for Oxygen Font is to design a clear, legible, sans
serif font which would be rendered with Freetype on Linux-based
devices. In addition a bold weight, plus regular and bold italics, and
a monospace version will be made.

## Design

Oxygen is to be constructed closely with the gridfitting aspects of
the Freetype engine. The Oxygen fonts will also be autohinted with
Werner Lemberg's "ttfautohint" library to further the compatibility
with the Freetype engine. The aim of this approach is to produce a
family of freetype-specific desktop fonts whose appearance will stay
uniform under different screen render settings, unlike more
traditionally designed 'screen fonts' that have tended to be designed
for best legibility on the Windows GDI render engine.

## License

The Oxygen Fonts are released under either The SIL Open Font License
(OFL) version 1.1 or the GNU General Public License version 3 with
font exception (GPL+FE).

Copyright 2011-2013 Vernon Adams vernnobile@gmail.com

## Testing

'Real world' user testing is vital. If you want to help test the
Oxygen Fonts please do so and send feedback.

## BRIEF DESCRIPTION OF FILES & FOLDERS

- 'in-progress' - warning! font file found here may be 'broken', have
  errors etc. These are the work-in-progress files. The main
  work-in-progress Oxygen Fonts are found in 'in-progress/Monospace',
- 'in-progress/Oxygen-Bold', 'in-progress/Oxygen-Regular', and
  'Oxygen-Italic'.

- 'version-0.2' - second milestone release, Monospace, Regular and Bold only.
- 'oxygen-fonts' - current release

- 'Contributions' - important contributions such as Cyrillic characters.
- 'GWF' - Google webfont versions of Oxygen Fonts (e.g. smaller character sets).
- 'tools' - extra development files used for metrics, kerning, encoding.
