KiCad symbols, footprints, and associated (usually 3rd party) 3D models that
I've needed to put together for projects.

# Recommended Usage

Add this library as a submodule of your project repo so you can pin the version
and avoid unintentionally incorporating changes:

```
git submodule add https://github.com/jmptable/kicad-parts.git
```

# Schematic Editing

## Default Fields

Preferences -> Eeschema -> Field Name Templates

Add the following defaults:

* Vendor - Mouser, Digi-Key, etc.
* Vendor Part Number - e.g. Digi-Key part number
* Vendor URL - Link to the page on the vendor's website. Check the box for URL.

_Having these values available in a standardized way in schematics makes it much
easier to create and check BOMs both by hand and in an automated fashion. The
latter is only straightforward when the field names match exactly._

## Symbols

* Always fill in the properties for new parts and symbols. _Having this
information available turns the symbol library into a resource for finding the
right part for a project, and also expediates design reviews._ Especially pay
attention to:
  - Datasheet
  - Description
* Always set the electrical type for symbol pins. _That makes it easier to check
that a schematic is correct and the designer's intention matches the design._
* Put an outline around the pin names and fill it with background color. _This
increases the readability of schematics which makes editing them more
efficient._
* For multiple power or ground pins, make one pin for every physical pin and
then set them all invisible except for one and place them all at the same
position (see this answer on [the KiCad forums](https://forum.kicad.info/t/can-a-single-schematic-pin-connect-to-multiple-footprint-pads/347/7)).
_Doing so makes it easier to make sure that every signal is correctly connected._

## Naming Conventions

* Always use the most generic prefix that uniquely identifies what is being
named (e.g. for a symbol put Xs for the portions of the part number that do not
affect the pinout). _Generic names make it easier to find and reuse symbols and
packages._
  - Usually the way to find the right name for a symbol is to go to the
  "Ordering Information" secion of the datasheet and fill in only the portions
  of the part number which affect the symbol.

### Library Names

* Always start the name with the "jmptable_" prefix. _This scheme is borrowed from
the [Digi-Key KiCad libraries](https://github.com/Digi-Key/digikey-kicad-library).
Adding a standard prefix makes it clear where a library came from and prevents
naming collisions (two libraries cannot have the same name)._
* Snake case with the first letter of each word capitalized and every letter
of acronyms capitalized. _Standardized naming schemes make it easier to find
what you are looking for. This one is the one that KiCad already uses._
* If there is a standard KiCad library for the same category then the name
should match exactly except for the prefix. _That way if you don't find what you
are looking for in one library you can go find the other equivalent libraries
that might have what you need._
* Footprints should use the footprint name and not the device name unless the
footprint is not of a standard type. _Footprints are usually generic and used
for many devices so being careful to refer to footprints by their proper names
can significantly reduce the time that would otherwise be spent recreating an
existing package that was missed because it was not given a standardized name._

# Contributing to This Read-Me

* Best practice for adding best practices is to explain the motivation for the
rule/practice (italisized). How does it help? What does it add? Why does the
benefit justify the effort? A great example of this in the wild in another
context is [the Airbnb JavaScript best practices guide](https://github.com/airbnb/javascript).
_Explaining motivations for rules facilitates critical review of them so they
can be removed or updated when necessary._

