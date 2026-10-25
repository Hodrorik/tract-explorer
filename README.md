# Tract Explorer

Look at brain tracts in 3D, learn their names, open your own tract files, and make tracts from a diffusion MRI scan, in a web page.

**Open it:** https://hodrorik.github.io/tract-explorer/

- **Nothing is uploaded.** Everything runs in your browser. Files you open stay on your device, and the page makes no request to any other address.
- **A learning and research tool, not for diagnosis.** Tracts made from a scan are candidates, not confirmed anatomy.
- The sample brain is the open HCP-1065 tract atlas (Yeh, 2022), not any real person's scan.

This repository holds only the built website (`index.html`, its fonts and the third-party notices in `NOTICE.md`). The source code, tests and notes are kept elsewhere.

## Third-party material

| What | Licence |
|---|---|
| HCP-1065 tract atlas (Yeh, 2022), used for the sample brain and for naming tracts | CC BY-SA 4.0 |
| three.js r128 (inside `index.html`) | MIT; its notice is kept at the top of the script |
| Albert Sans, Atkinson Hyperlegible, IBM Plex Mono (`fonts/`) | SIL Open Font License 1.1; the licence texts are in `fonts/` |
| Code ported from DIPY (noise reduction, ringing removal, CSD, probabilistic tracking, false-tract removal, tract profiles, tissue classes), inside `index.html` | BSD 3-Clause; full notice in `NOTICE.md` |
| Code ported from MRtrix3 (anatomy-aware tracking, SIFT2 weights), inside `index.html` as readable source | Mozilla Public License 2.0, those parts only; full notice in `NOTICE.md` |
| Region atlases for the connection table (Schaefer 2018, Tian 2020, Diedrichsen 2009, Iglesias 2015 brainstem), inside `index.html` | MIT / public domain / CC BY / FreeSurfer licence; details in `NOTICE.md` |

The Tract Explorer code itself has no open licence yet.
