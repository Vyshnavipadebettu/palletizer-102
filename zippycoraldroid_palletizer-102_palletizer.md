# Model zippycoraldroid:palletizer-102:palletizer

Provide a description of the model and any relevant information.

## Configuration
The following attribute template can be used to configure this model:
{
  "columns": <int>,
  "rows": <int>,
  "layers": <int>,
  "box_height_mm": <float>
}

### Attributes

The following attributes are available for this model:

| Name          | Type   | Inclusion | Description                |
|---------------|--------|-----------|----------------------------|
| columns       | int    | Required  | Boxes across the pallet    |
| rows          | int    | Required  | Boxes deep                 |
| layers        | int    | Required  | Stacked layers             |
| box_height_mm | float  | Required  | Box height, above zero     |

### Example Configuration

{
  "columns": 2,
  "rows": 2,
  "layers": 2,
  "box_height_mm": 100
}

## DoCommand

If your model implements DoCommand, provide an example payload of each command that is supported and the arguments that can be used. If your model does not implement DoCommand, remove this section.

This model is driven through DoCommand. Every command names its verb with the command key.

Verb	Does	Answers
status	Reports the resources it resolved	{"resources": {...}, "boxes_packed": <int>}
clear	Empties the pallet, the scene, and the record	{"cleared": true}
pick	Picks the next box off the pick-station	{"picked": true}
place	Places the held box in the next slot	{"slot": <int>}
pack	Packs the whole pattern, from empty	{"placed": <int>}
An unrecognized verb answers:

{
  "error": "unknown command: <verb>"
}

### Example DoCommand

{
  "command": "pack"
}

