# Third-party material

| What | Where | Licence |
|---|---|---|
| HCP-1065 tract atlas (Yeh, 2022) | `prototype/atlas_sample.json`, `prototype/atlas_ref.json`, `testdata/yeh2022.trx` | CC BY-SA 4.0. Credit it wherever it is shown; anything built from it is shared under the same terms |
| Schaefer 2018 cortical parcellation, 100 parcels, 7 networks (Schaefer et al., 2018, doi:10.1093/cercor/bhx179), from the CBIG repository | `prototype/regions_atlas.json` (labels 17 to 116, on the MNI152 2009c 2 mm grid; names rewritten in plain words by `prototype/make_regions.js`) | MIT (text below) |
| Melbourne Subcortex Atlas, scale I (Tian et al., 2020, doi:10.1038/s41593-020-00711-6), combined with the Schaefer parcellation by its authors (github.com/yetianmed/subcortex) | `prototype/regions_atlas.json` (labels 1 to 16) | Public domain; publications using it cite Tian et al. (2020) |
| Probabilistic atlas of the cerebellar lobules and deep nuclei (Diedrichsen et al., 2009, doi:10.1016/j.neuroimage.2009.01.045; Diedrichsen et al., 2011, doi:10.1016/j.neuroimage.2010.10.035), `atl-Anatom` in MNI152 2009c symmetric space from github.com/DiedrichsenLab/cerebellar_atlases (Diedrichsen_2009) | `prototype/regions_atlas.json` (labels 117 to 147). Changed: moved onto the 2 mm grid of the asymmetric template (each 2 mm voxel takes the part most of its eight 1 mm voxels hold), both fastigial nuclei and the vermis part of crus I left out as too small, voxels the cortical and deep regions already hold left to them, names rewritten in plain words (`prototype/make_regions.js`) | Creative Commons Attribution (CC BY), as the collection's README states for atlases whose paper says nothing else (no version stated; the current one is https://creativecommons.org/licenses/by/4.0/) |
| Brainstem subdivision (midbrain, pons, medulla, superior cerebellar peduncle; Iglesias et al., 2015, doi:10.1016/j.neuroimage.2015.02.065), probability maps in ICBM 2009c symmetric space from FreeSurfer (https://surfer.nmr.mgh.harvard.edu/fswiki/SubfieldAtlasesICBMspace, Brainstem.zip) | `prototype/regions_atlas.json` (labels 148 to 151). Changed: each 2 mm voxel takes the part with the highest mean probability over its eight 1 mm voxels, if above that of none; laid on the asymmetric template's grid; names rewritten in plain words | FreeSurfer Software License, Part B (text below, and in `regions_atlas.json` as `terms`) |
| three.js r128 | `prototype/three.min.js` | MIT |
| Albert Sans, Atkinson Hyperlegible, IBM Plex Mono | `prototype/fonts`, `site/fonts` | SIL Open Font License 1.1 (licence texts are in the fonts folder) |
| Other files in `testdata/` | From the NiiVue project's demo images, except the three `synthetic_*.trk` files made for these tests | Check each file's own terms before this repository is made public |
| DIPY's MP-PCA denoising (`dipy/denoise/localpca.py`: `genpca`, `mppca`, `_pca_classifier`) | Ported to JavaScript in `prototype/denoise.js` | BSD 3-Clause (text below) |
| DIPY's constrained spherical deconvolution (`dipy/reconst/csdeconv.py`: `ConstrainedSphericalDeconvModel`, `csdeconv`, `response_from_mask_ssst`, `mask_for_response_ssst`, `estimate_response`; `dipy/reconst/shm.py`: `real_sh_descoteaux_from_index`, `sph_harm_ind_list`, `sh_to_rh`) | Ported to JavaScript in `prototype/tracker.js` (`csdJob`, `shBasis`) | BSD 3-Clause (text below) |
| DIPY's multi-shell, multi-tissue CSD (`dipy/reconst/mcsd.py`: `mask_for_response_msmt`, `response_from_mask_msmt`, `multi_shell_fiber_response`, `multi_tissue_basis`, `MultiShellDeconvModel`, `_inflate_response`, `_basic_delta`) | Ported to JavaScript in `prototype/tracker.js` (`msmtJob`); DIPY's cvxpy solve is replaced by Lawson and Hanson's NNLS on the least-distance form (`ldpNnls`), written from their book (Solving Least Squares Problems, 1974, ch. 23) | BSD 3-Clause (text below) |
| DIPY's probabilistic tracking (`dipy/direction/probabilistic_direction_getter.pyx`: `ProbabilisticDirectionGetter.get_direction_c`; `dipy/direction/closest_peak_direction_getter.pyx`: `_get_pmf`; `dipy/direction/pmf.pyx`: `SHCoeffPmfGen.get_pmf_c`) | Ported to JavaScript in `prototype/tracker.js` (`trackJob` with `tracking: 'prob'`) | BSD 3-Clause (text below) |
| DIPY's Gibbs ringing removal (`dipy/denoise/gibbs.py`: `gibbs_removal`, `_gibbs_removal_2d`, `_gibbs_removal_1d`, `_image_tv`, `_weights`; written by Rafael Neto Henriques) | Ported to JavaScript in `prototype/degibbs.js` | BSD 3-Clause (text below) |
| DIPY's hidden Markov random field tissue classifier (`dipy/segment/tissue.py`: `TissueClassifierHMRF.classify`; `dipy/segment/mrf.pyx`: `ConstantObservationModel`, `IteratedConditionalModes`) | Ported to JavaScript in `prototype/t1.js` (`hmrf`) | BSD 3-Clause (text below) |
| MRtrix3 3.0.4 anatomically-constrained tractography (`src/dwi/tractography/ACT/tissues.h`, `method.h`, `gmwmi.cpp`; `tracking/exec.h`: `gen_track_unidir`, `apply_priors`, `truncate_exit_sgm`, the ACT seed checks; `tracking/method.cpp`: `truncate_track`; `seeding/gmwmi.cpp`; `cmd/5tt2gmwmi.cpp`; Copyright (c) 2008-2024 the MRtrix3 contributors) | Ported to JavaScript in `prototype/act.js`, which is therefore under the Mozilla Public License 2.0 (notice below); the rest of the project is not | MPL 2.0: `act.js` and changes to it stay under MPL 2.0 and their source must be available to anyone who gets them (the page ships it as readable source). It can be combined with code under other terms, including closed or paid code, file by file |
| MRtrix3 3.0.4 SIFT2 streamline weights (`cmd/tcksift2.cpp`; `src/dwi/tractography/SIFT2/`: `tckfactor.cpp`, `coeff_optimiser.cpp`, `line_search.cpp`, `fixel_updater.cpp`, `reg_calculator.cpp`, `regularisation.h`, `fixel.h`; `src/dwi/tractography/SIFT/`: `model_base.h`, `model.h`, `proc_mask.cpp`, `track_contribution.h`; `src/dwi/fmls.cpp`, `fmls.h`; `src/dwi/tractography/mapping/mapper.h` (`voxelise_precise`); `core/math/hermite.h`; the 1281-direction set of `src/dwi/directions`; Copyright (c) 2008-2024 the MRtrix3 contributors) | Ported to JavaScript in `prototype/sift2.js`, which is therefore under the Mozilla Public License 2.0 (notice below) | MPL 2.0, as for `act.js`: `sift2.js` and changes to it stay under MPL 2.0 and their source must be available to anyone who gets them (the page ships it as readable source); it can be combined with code under other terms, file by file |
| DIPY's cluster confidence index (`dipy/tracking/streamline.py`: `cluster_confidence`) | Ported to JavaScript in `prototype/recognize.js` (`pruneJob`) | BSD 3-Clause (text below) |
| DIPY's RecoBundles (`dipy/segment/bundles.py`: `RecoBundles.recognize`, `_prune_what_not_in_model`), its steps for keeping only streamlines that match an atlas tract and dropping groups off a tract's core | Ported to JavaScript in `prototype/recognize.js` (`filterJob`, `coreKeep`, `trimToCore`); DIPY's whole-brain grouping before the search and its per-tract registration (local SLR) are left out | BSD 3-Clause (text below) |
| DIPY's tract profiles (`dipy/stats/analysis.py`: `afq_profile`, `gaussian_weights`; `dipy/tracking/streamline.py`: `orient_by_streamline`, `values_from_volume`; the one-cluster QuickBundles centroid of its AFQ example) | Ported to JavaScript in `prototype/ingest.js` (`tractMeasures`) | BSD 3-Clause (text below) |

Used by a check only, never shipped and not stored here: the ISMRM 2015 Tractography Challenge data (Maier-Hein et al., 2017; Zenodo 572345, CC BY 4.0), its 2023 scoring data (Renauld et al., 2023) and 2015 scoring code (Zenodo 810130), and scilpy (MIT). `prototype/check_ismrm2015.py` runs them from a separate folder.

The tracking, naming and correction code was written from scratch. It follows published methods and copies no code from DSI Studio, DIPY, MRtrix3, FSL or dwi2trx. The exceptions are anatomy-aware tracking (`prototype/act.js`) and the SIFT2 streamline weights (`prototype/sift2.js`), ported from MRtrix3 under its Mozilla Public License, and the noise reduction (`prototype/denoise.js`), the ringing removal (`prototype/degibbs.js`), constrained spherical deconvolution (`csdJob` and `msmtJob` in `prototype/tracker.js`), probabilistic tracking (`tracking: 'prob'` in `prototype/tracker.js`), the removal of false streamlines and of false bundles (`pruneJob`, `filterJob` and `coreKeep` in `prototype/recognize.js`), the tract profiles (`tractMeasures` in `prototype/ingest.js`) and the T1 tissue classes (`hmrf` in `prototype/t1.js`), ports of DIPY's code under DIPY's BSD licence.

The connection table's end rule follows DIPY's `connectivity_matrix` and the idea of MRtrix3's `tck2connectome` radial search (Smith et al., 2015, doi:10.1016/j.neuroimage.2014.10.004); it was written from the description, not ported.

Methods followed: Jeurissen et al. 2014 (multi-shell, multi-tissue CSD, doi:10.1016/j.neuroimage.2014.07.061), as ported from DIPY, solved with Lawson & Hanson 1974 (NNLS and least-distance programming, ch. 23), written from the book for `ldpNnls` in `prototype/tracker.js` (MRtrix3's `dwi2fod msmt_csd` and its own solver are used only as a referee by `check_mrtrix_mcsd.py`, not shipped); Zhang, Brady & Smith 2001 (hidden Markov random field tissue classes, doi:10.1109/42.906424); Tustison et al. 2010 (N4 bias field correction, doi:10.1109/TMI.2010.2046908) and Sled et al. 1998 (N3, doi:10.1109/42.668698), written from the papers for `biasField` in `prototype/t1.js` (no ANTs or ITK code; ITK's N4 in SimpleITK is used only as a referee by `check_dipy_t1.py`, not shipped); Felzenszwalb & Huttenlocher 2012 (exact distance transform, doi:10.4086/toc.2012.v008a019, `distance` in `prototype/t1.js`); Mattes et al. 2003 (mutual information with a B-spline Parzen window and its gradient, doi:10.1109/TMI.2002.803111), Nocedal 1980 (L-BFGS, doi:10.1090/S0025-5718-1980-0572855-7), Wang et al. 2017 (registering the b=0 image to a T1 instead of a field map, doi:10.3389/fninf.2017.00017) and Esteban et al. 2019 (fieldmap-less "SyN-SDC" restricted to the phase-encoding direction, fMRIPrep, doi:10.1038/s41592-018-0235-4), written from the papers for `prototype/unwarp.js` (no ANTs, ITK, sdcflows or FSL code; FSL topup is used only as a referee by `check_fieldmap.py`, not shipped); Smith et al. 2012 (anatomically constrained tractography and its five-tissue-type layout, doi:10.1016/j.neuroimage.2012.06.005; its rules are ported from MRtrix3 into `prototype/act.js`, see above); Smith et al. 2015 (SIFT2, doi:10.1016/j.neuroimage.2015.06.092) and Smith et al. 2013 (SIFT and its fixel model, doi:10.1016/j.neuroimage.2012.11.049), ported from MRtrix3 into `prototype/sift2.js`; Raffelt et al. 2012 (FOD lobes and their integrals, FMLS / apparent fibre density, doi:10.1016/j.neuroimage.2011.10.084); Veraart et al. 2016 (MP-PCA noise reduction); Kellner et al. 2016 (Gibbs ringing removal by local subvoxel shifts); Manjón et al. 2013 (weighting overlapping blocks); Yeh et al. 2010 (generalized q-sampling imaging); Tournier et al. 2007 (constrained spherical deconvolution, doi:10.1016/j.neuroimage.2007.02.016); Yeh et al. 2013 (QA-based deterministic tracking); Garyfallidis et al. 2014 (DIPY, whose probabilistic tracking is ported); Garyfallidis et al. 2012, 2015, 2018 (QuickBundles, streamline-based registration, RecoBundles); Studholme et al. 1999 (normalised mutual information); Leemans & Jones 2009 (rotating gradient directions after motion correction); Jordan et al. 2018 (cluster confidence index, doi:10.1111/jon.12467); Yeatman et al. 2012 (tract profiles, doi:10.1371/journal.pone.0049790); Yeh 2020 (span and curl of a tract, doi:10.1016/j.neuroimage.2020.117329).

### DIPY licence (for `prototype/denoise.js`, `prototype/degibbs.js`, the CSD (single- and multi-shell) and probabilistic tracking parts of `prototype/tracker.js`, `pruneJob`, `filterJob`, `coreKeep` and `trimToCore` in `prototype/recognize.js`, `tractMeasures` in `prototype/ingest.js` and `hmrf` in `prototype/t1.js`)

```
Copyright (c) 2008-2026, dipy developers
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are
met:

    * Redistributions of source code must retain the above copyright
       notice, this list of conditions and the following disclaimer.

    * Redistributions in binary form must reproduce the above
       copyright notice, this list of conditions and the following
       disclaimer in the documentation and/or other materials provided
       with the distribution.

    * Neither the name of the dipy developers nor the names of any
       contributors may be used to endorse or promote products derived
       from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
"AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

### CBIG licence (for the Schaefer 2018 parcellation in `prototype/regions_atlas.json`)

```
Copyright (c) 2016 Computational Brain Imaging Group (CBIG)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```

### FreeSurfer Software License, Part B (for the brainstem parts in `prototype/regions_atlas.json`)

From https://surfer.nmr.mgh.harvard.edu/fswiki/FreeSurferSoftwareLicense (version 1.0, February 2011), which asks for all of Part B to go with any copy.

```
All or portions of this licensed product (such portions are the "Software") have been obtained under license from The General Hospital Corporation and are subject to the following terms and conditions:

PART B. DOWNLOADING AGREEMENT
License from MGH with Right to Sublicense ("Software License")

 1. As used in this Software License, "you" means the individual downloading and/or using, reproducing, modifying, displaying and/or distributing the Software and the institution or entity which employs or is otherwise affiliated with such individual in connection therewith.  The General Hospital Corporation, Boston MA, USA ("MGH") hereby grants you, with right to sublicense, with respect to MGH's rights in the software, and data, if any, which is the subject of this Software License (collectively, the "Software"), a royalty-free, non-exclusive license to use, reproduce, make derivative works of, display and distribute the Software, provided that: (a) you accept and adhere to all of the terms and conditions of this Software License; (b) in connection with any copy of or sublicense of all or any portion of the Software, all of the terms and conditions in this Software License shall appear in and shall apply to such copy and such sublicense, including without limitation all source and executable forms and on any user documentation, prefaced with the following words: "All or portions of this licensed product (such portions are the "Software") have been obtained under license from The General Hospital Corporation and are subject to the following terms and conditions:" (c) you preserve and maintain all applicable attributions, copyright notices and licenses included in or applicable to the Software; (d) modified versions of the Software must be clearly identified and marked as such, and must not be misrepresented as being the original Software; and (e) you consider making, but are under no obligation to make, the source code of any of your modifications to the Software freely available to others on an open source basis.

 2. The license granted in this Software License includes without limitation the right to (i) incorporate the Software into proprietary programs (subject to any restrictions applicable to such programs), (ii) add your own copyright statement to your modifications of the Software, and (iii) provide additional or different license terms and conditions in your sublicenses of modifications of the Software; provided that in each case your use, reproduction or distribution of such modifications otherwise complies with the conditions stated in this Software License.

 3. This Software License does not grant any rights with respect to third party software, except those rights that MGH has been authorized by a third party to grant to you, and accordingly you are solely responsible for (i) obtaining any permissions from third parties that you need to use, reproduce, make derivative works of, display and distribute the Software, and (ii) informing your sublicensees, including without limitation your end-users, of their obligations to secure any such required permissions.

 4. The Software has been designed for research purposes only and has not been reviewed or approved by the Food and Drug Administration or by any other agency. YOU ACKNOWLEDGE AND AGREE THAT CLINICAL APPLICATIONS ARE NEITHER RECOMMENDED NOR ADVISED. Any commercialization of the Software is at the sole risk of the party or parties engaged in such commercialization. You further agree to use, reproduce, make derivative works of, display and distribute the Software in compliance with all applicable governmental laws, regulations and orders, including without limitation those relating to export and import control.

 5. The Software is provided "AS IS" and neither MGH nor any contributor to the software (each a "Contributor") shall have any obligation to provide maintenance, support, updates, enhancements or modifications thereto. MGH AND ALL CONTRIBUTORS SPECIFICALLY DISCLAIM ALL EXPRESS AND IMPLIED WARRANTIES OF ANY KIND INCLUDING, BUT NOT LIMITED TO, ANY WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NON-INFRINGEMENT. IN NO EVENT SHALL MGH OR ANY CONTRIBUTOR BE LIABLE TO ANY PARTY FOR DIRECT, INDIRECT, SPECIAL, INCIDENTAL, EXEMPLARY OR CONSEQUENTIAL DAMAGES HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY ARISING IN ANY WAY RELATED TO THE SOFTWARE, EVEN IF MGH OR ANY CONTRIBUTOR HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES. TO THE MAXIMUM EXTENT NOT PROHIBITED BY LAW OR REGULATION, YOU FURTHER ASSUME ALL LIABILITY FOR YOUR USE, REPRODUCTION, MAKING OF DERIVATIVE WORKS, DISPLAY, LICENSE OR DISTRIBUTION OF THE SOFTWARE AND AGREE TO INDEMNIFY AND HOLD HARMLESS MGH AND ALL CONTRIBUTORS FROM AND AGAINST ANY AND ALL CLAIMS, SUITS, ACTIONS, DEMANDS AND JUDGMENTS ARISING THEREFROM.

 6. None of the names, logos or trademarks of MGH or any of MGH's affiliates or any of the Contributors, or any funding agency, may be used to endorse or promote products produced in whole or in part by operation of the Software or derived from or based on the Software without specific prior written permission from the applicable party.

 7. Any use, reproduction or distribution of the Software which is not in accordance with this Software License shall automatically revoke all rights granted to you under this Software License and render Paragraphs 1 and 2 of this Software License null and void.

 8. This Software License does not grant any rights in or to any intellectual property owned by MGH or any Contributor except those rights expressly granted hereunder.
```

### MRtrix3 licence notice (for `prototype/act.js` and `prototype/sift2.js`)

```
Copyright (c) 2008-2024 the MRtrix3 contributors.

This Source Code Form is subject to the terms of the Mozilla Public
License, v. 2.0. If a copy of the MPL was not distributed with this
file, You can obtain one at http://mozilla.org/MPL/2.0/.

Covered Software is provided under this License on an "as is"
basis, without warranty of any kind, either expressed, implied, or
statutory, including, without limitation, warranties that the
Covered Software is free of defects, merchantable, fit for a
particular purpose or non-infringing.
See the Mozilla Public License v. 2.0 for more details.

For more details, see http://www.mrtrix.org/.
```
