The following comes from the Sumarac et al 2024 paper:

Features to Extract:
* median firing rate
* burst index
* coefficient of variation
* spike-train oscillatory power
* average oscillatory burst duration
these were all across different frequency bands: theta (4-8Hz), alpha (8-12 Hz), low beta (12-21Hz), high beta (21-30Hz).

Firing Rate: inverse of mean interspike interval distribution (Fig3a)

Burst Index: ratio of means from a two-component Gaussian mixture model applied to the log interspike interval distribution (fig 3aa)

Coefficient of variation: dividing the median absolute deviation of the interspike interval distribution by its median (fig 3a)

Oscillatory power: Lomb’s periodogram, conducted on he autocorrelation function of single neuron segments (fig3b)

Oscillatory burst detection:
* trying to determine the duration of time a neuron spent spontaneously bursting within a specific frequency range (fig 3c)
* Spiketrain of a neuron converted into a binary sequence then downsampled to 500Hz
* filtered binary sequence into the frequency band of interest (ranging from theta to high beta using 4th order zero-phase Butterworth filter)
    * this converts spiketrain into LFP-like signal

Burst determination:
* classifies burst durations when oscillatory activity surpasses the overall noise floor within a recording
* envelop filtered binary sequency in ea. frequency band using the absolute value of the Hilbert transform
* oscillatory burst identified when amplitude surpasses a threshold for more than 100ms, defined as 4x the median of averaged peaks from envelopes of five overlapping 6Hz bands in the low gamma band (45-55Hz) from the same MER segment
* gamma waveforms determined using filtered binary sequence approach
* then extract average burst duration (time spent above the determined threshold)

Note: SpookySpikes is a GUI used to visualize single MERs.
https://github.com/Toronto-TNBS/spooky-spikes

