# UGig 75801042 Final Delivery

Prepared for accepted gig `75801042-7446-4347-905d-3f761ed77f82` (`10 USDC`). This package contains the complete 100-track metadata and original metal-conversion prompt set.

## Files

- `tracks.csv` - spreadsheet-friendly delivery with one row per playlist position.
- `tracks.json` - the same 100 records as a JSON array.

Both files use these required fields:

`position`, `title`, `artists`, `duration`, `inferred_source_style`, `inferred_mood`, `inferred_energy`, `inferred_tempo_band`, `metal_conversion_direction`, `lyric_theme_direction`, `suno_prompt`.

## Source

- Public Spotify embed: <https://open.spotify.com/embed/playlist/2FrXlq6ChSIFJ6CyGS0PGI>
- Playlist label shown by the embed: `Mosh Coding Songs` by `moshcoding`.
- Retrieved through a live web read on `2026-07-10`.
- The visible embed sequence contained exactly 100 positions. Titles, displayed artist credits, durations, order, capitalization, and exact duplicates were transcribed from that sequence.

The buyer's tokenized playlist-sharing URL is intentionally not reproduced here. The public embed above is sufficient provenance for this delivery.

## Methodology

1. Read positions `1..100` from the live public embed and captured only visible factual metadata: title, displayed artists, and displayed duration.
2. Preserved the source order and did not collapse duplicates. Positions `66` and `67` are both `Not Broken` by `CortexUS`, duration `03:22`.
3. Added creative planning fields from title and artist metadata only. Narrative scenarios were independently invented from generic title concepts rather than adapted from source-song plots. No audio was downloaded, played, fingerprinted, or analyzed.
4. Prefixed every style, mood, energy, tempo, and lyric-theme observation with `Title/artist-informed creative inference:` so it cannot be mistaken for measured or authoritative metadata.
5. Used qualitative tempo bands such as `slow-feel`, `mid-tempo feel`, and `brisk-feel`. No BPM is stated or implied to have been measured.
6. Wrote each Suno prompt as an original production brief using genre, arrangement, instrumentation, vocal, structure, and a newly invented scenario or thematic direction. Prompts do not ask for imitation of any named artist.

## Copyright-Safe Boundary

- No lyrics were copied, quoted, summarized line by line, or reconstructed.
- No melody, chord progression, recording, stem, or audio feature was extracted.
- Track titles, displayed artist credits, positions, and durations are treated as factual playlist metadata.
- The creative directions are transformations at the level of general genre, mood, arrangement, and original theme. They are not claims about the recordings' measured musical properties.
- Any final generated song should use a new melody and entirely original lyrics. Review outputs for accidental resemblance before commercial use and follow the generation platform's current terms and licensing rules.

## Suggested Suno Workflow

1. Select a row and use `suno_prompt` as the production brief.
2. Draft entirely new lyrics from `lyric_theme_direction`; do not paste or adapt lyrics from the referenced track.
3. Generate at least two variants, then compare structure, vocal fit, riff clarity, and separation from the reference metadata.
4. Refine with generic production language from `metal_conversion_direction`, such as guitar tuning feel, drum character, dynamics, vocal approach, and section shape.
5. Keep artist names out of generation prompts. Describe the desired musical result directly.
6. Perform a final human originality, safety, and rights review before sharing or releasing an output.

## Validation Counts

- JSON records: `100`
- CSV data rows: `100`
- Required fields per record: `11`
- Required non-empty values checked: `1100`
- Position range: every integer from `1` through `100`, once each
- Exact source duplicate groups preserved: `1`
- Rows in the preserved duplicate group: positions `66` and `67`
- CSV/JSON metadata and inference fields: match row for row

Local validation parses both files, compares all rows, verifies the counts above, and fails if a required value is blank or either duplicate position is removed.
