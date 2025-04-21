# StreetSim-EEG-Gaze

This repo coincides with our submission to SIGSIM PADS '25 [PhD Colloquium](https://sigsim.acm.org/conf/pads/2025/blog/phd-colloquium/), hosted from June 23-26, 2025. This repo contains the necessary code to post-process EEG data and gaze tracking data from a VR simulation using the _Meta Quest Pro_ and _Muse S_ BCI.

This repo consists of two separate Python notebooks: 

* `participant_filtering.ipynb`: Gives us an idea of which participants' EEG are suitable (or not) for our analysis.
* `main.ipynb`: The main notebook for finding correlations between features and EEG frequencies.

Either notebook is not necessarily dependent on the other; you can run them separately. However, both make some assumptions about how the data is supplied to either notebook:

1. All user data must be stored in a `data/` directory.
2. Within the `data/` directory, each participant has their own unique folder, with the naming convention `P<#>`. For example, participant 1 has a folder `data/P1/`.
3. Within each participant folder, it expects to see the following files:
    * `eeg_rest.csv`: The resting state EEG, measured for 30 seconds or more.
    * `eeg_vr.csv`: The EEG data collected during trials.
    * `eye.csv`: The eye tracking data collected from the _Meta Quest Pro_.
    * `positions.csv`: The position/trajectory data of all entities in the simulation space. This includes the user themselves.
    * `trials.csv`: A list of trials executed by the participant.

There are some additional code files present:

* `debugging_code.ipynb`: debugging code that is the prototype of both `participant_filtering.ipynb` and `main.ipynb`. Not really used, present for posterity.
* `helpers.py`: helper functions and variables used by both `participant_filtering.ipynb` and `main.ipynb`.

When you run either `participant_filtering.ipynb` and `main.ipynb`, they will spit out figures inside the `data/` directory. For `participant_filtering.ipynb`, it will auto-generate an output directory with the naming convention `data/outputs_filtering_<YYYY>-<MM>-<<DD>_<HH>-<MM>-<SS>/`. The same is with `main.ipynb`, except the output directory name is `data/outputs_correlations_<YYYY>-<MM>-<<DD>_<HH>-<MM>-<SS>/`. These folders are generated every time you first run the notebooks, so no need to create them manually.
