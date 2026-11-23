# LabVIEW J1939 Signal Filter

The current prototype decodes and validates **Engine Speed (SPN 190)** from a manually entered **EEC1 payload (PGN 61444 / 0xF004)**. It runs in LabVIEW with simulated inputs and requires no CAN hardware.

## Current implementation

- Accepts a payload as an array of unsigned 8-bit values (`U8`).
- Extracts the low byte from array index `3` and the high byte from index `4`.
- Displays the decoded engine speed in RPM.
- Reports `Pass` and turns on the `Signal Valid?` LED when the payload contains exactly eight bytes and the decoded RPM is within the configured limits.

## Decoding and validation

EEC1 stores engine speed in payload bytes 4 and 5, counting from 1. The resolution is **0.125 RPM/count** and the offset is **0 RPM**.

```text
Raw count  = Byte 4 + (Byte 5 × 256)
Engine RPM = Raw count × 0.125
```

The VI uses `Index Array` to extract the bytes, `Array Size` to check the payload length, and `In Range and Coerce` to check the decoded RPM. A Boolean `AND` combines the length and range checks. The demo uses an inclusive **0–3000 RPM** validation range.

## Run the demo

1. Open `J1939_Signal_Validator.vi` in NI LabVIEW.
2. On the Front Panel, enter the decimal values below into `EEC1 Payload`, starting at array index `0`.
3. Run the VI and check the decoded RPM, `Validation Result`, and `Signal Valid?` LED.

| EEC1 payload (decimal) | Decoded RPM | Expected result |
| --- | ---: | --- |
| `0, 0, 0, 192, 93, 0, 0, 0` | 3000 | Pass, LED on |
| `0, 0, 0, 200, 93, 0, 0, 0` | 3001 | Fail, LED off |

## Planned features

- Add a PGN filter that routes EEC1 frames (`61444`) to the decoder and marks other PGNs as ignored.
- Replay mixed simulated J1939 frames from a CSV file and report the result for each frame.
