# FAQ

## Can I still use the auto calibrate features?

A: Unfortunately, at this time they are not supported. No.

## When I print from the side spool, the printer still acts like I'm using the CFS

A: This is an issue with the k2-improvements.  We suspect it has something to do with the moonraker update and are investigating.

For now an a work around is to remove this line from your machine start g-code when using the side spool:

```raw
T[initial_no_support_extruder]
```

## Fluidd seems to hang at 99% even though the print appears to have finished

A: It apepars that this is an issue with Creality Print not placing a newline at the end of the sliced gcode.
