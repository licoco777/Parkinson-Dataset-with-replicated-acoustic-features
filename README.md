# Parkinson-Dataset-with-replicated-acoustic-features
Contains acoustic features extracted from 3 voice recording replications of the sustained /a/ phonation for each one of the 80 subjects (40 of them with Parkinson's Disease).
# Dataset's Story

Contains acoustic features extracted from 3 voice recording replications of the sustained /a/ phonation for each one of the 80 subjects (40 of them with Parkinson's Disease).

## Source links
https://archive-beta.ics.uci.edu/ml/datasets/parkinson+dataset+with+replicated+acoustic+features
https://archive.ics.uci.edu/ml/machine-learning-databases/00489/

## Explanation of Variables

* 1. __ID__:  Subjects's identifier. 

* 2. __Recording__: Number of the recording. 

* 3. __Status__: 0=Healthy; 1=PD 

* 4. __Gender__: 0=Man; 1=Woman 

* 5. __Pitch local perturbation measures__: __Jitter_rel__: relative jitter, __Jitter_abs__:absolute jitter, __Jitter_RAP__: relative average perturbation, __Jitter_PPQ__: pitch perturbation quotient.

* 6. __Amplitude perturbation measures__: __Shim_loc__: local shimmer, __Shim_dB__: shimmer in dB, __Shim_APQ3__: 3-point amplitude perturbation quotient, __Shim_APQ5__: 5-point amplitude perturbation quotient, __Shim_APQ11__: 11-point amplitude perturbation quotient.

* 7. __Harmonic-to-noise ratio measures__: __HNR05__: harmonic-to-noise ratio in the frequency band 0-500 Hz , __HNR15__: in 0-1500 Hz , __HNR25__: in 0-2500 Hz , __HNR35__: in 0-3500 Hz (), __HNR38__: in 0-3800 Hz. 

* 8. Mel frequency cepstral coefficient-based spectral measures of order 0 to 12 (__MFCC0, MFCC1,..., MFCC12__) and their derivatives (__Delta0, Delta1,..., Delta12__). 

* 9. __RPDE__: Recurrence period density entropy. 

* 10. __DFA__: Detrended fluctuation analysis. 

* 11. __PPE__: Pitch period entropy. 

* 12. __GNE__: Glottal-to-noise excitation ratio.

## Additional Information

_Important remarks before using this dataset:_

__1.__ _Each row can not be used independently, because is one of the three replications of one individual. Nature of data is dependent for each subject, but independent from one to another subject. So, traditional technique from machine learning can not be applied to this dataset, because those techniques are based on the independent nature of the instances. There are 240 instances but for only 80 subjects, so they are not independent. Techniques as those presented in Naranjo et al. (2016), Naranjo et al. (2017) or other specifically designed can be used._

__2.__ _The concept of replication considered here does not match the classical concept of statistical repeated measurements. The term 'replications' refers to the collection of features extracted from voice recordings belonging to the same subject. Since, in this context, features are extracted from multiple consecutive voice recordings from the same subject, in principle, the features should be identical. The imperfections in technology and the own biological variability result in non-identical replicated features that are more similar to one another than features from different subjects._

__3.__ _All information about how the dataset was generated is presented in Naranjo et al. (2016)._

_Relevant Papers:_

_Naranjo, L., PÃ©rez, C.J., Campos-Roca, Y., MartÃ­n, J.: Addressing voice recording replications for Parkinsonâ€™s disease detection. Expert Systems With Applications 46, 286-292 (2016)_
https://pubmed.ncbi.nlm.nih.gov/27209185/

_Naranjo, L., PÃ©rez, C.J., MartÃ­n, J., Campos-Roca, Y.: A two-stage variable selection and classification approach for Parkinsonâ€™s disease detection by using voice recording replications. Computer Methods and Programs in Biomedicine 142, 147-156 (2017)_
https://pubmed.ncbi.nlm.nih.gov/28325442/


## Data Scientist's Notes

### A Short Brief About Variables for Unfamiliar with the Field:

__ID:__ 

_The ID is a number assigned to the identity of the subjects._

However, since there were three separate records for each subject, one subject was kept as three different identities. So it looks like I will have to do a new operation on the ID. And based on the following explanation I quoted from above(Additional Information), I can grouping inside of ID and reduce the one subject's records to one.

_"Each row can not be used independently, because is one of the three replications of one individual. Nature of data is dependent for each subject, but independent from one to another subject."_

__Recording:__ 

_Number of the recording of the subjects_

__Pitch local perturbation measures__:

__Jitter_rel__:relative jitter,

__Jitter_abs__:absolute jitter,

__Jitter_RAP__: relative average perturbation,

__Jitter_PPQ__: pitch perturbation quotient

AND

__Amplitude perturbation measures__: 

__Shim_loc__: local shimmer, 

__Shim_dB__: shimmer in dB, 

__Shim_APQ3__: 3-point amplitude perturbation quotient, 

__Shim_APQ5__: 5-point amplitude perturbation quotient, 

__Shim_APQ11__: 11-point amplitude perturbation quotient


For the methods of measurements:

https://www.fon.hum.uva.nl/praat/manual/Voice_2__Jitter.html

https://www.fon.hum.uva.nl/praat/manual/Voice_3__Shimmer.html

For more detailed information:

"Jitter and shimmer are measures of the cycle-to-cycle variations
of fundamental frequency and amplitude, respectively, which
have been largely used for the description of pathological voice
quality. Since they characterise some aspects concerning
particular voices, it is a priori expected to find differences in the values of jitter and shimmer among speakers. In this paper,
several types of jitter and shimmer measurements have been
analysed. Experiments performed with the Switchboard-I
conversational speech database show that jitter and shimmer
measurements give excellent results in speaker verification as
complementary features of spectral and prosodic parameters." [1]

"Jitter is noise in the temporal or timing domain.
Yes, it really is that simple. Normally though we apply the term to electrical or optical signals we can measure with oscilloscopes or other time measurement equipment.
We can think of jitter two ways.
• As an instantaneous effect: This one edge isn’t where I wanted it to be.
• As an accumulation of effects: in this series of edges, each edge is displaced an equal amount,
and the last edge shows the sum of the displacement times. "[2]

"The most important vocal acoustic parameters for
clinical use are measurements of noise, vocal extension
profile, acoustic spectrography, fundamental frequency and
perturbation index - jitter and shimmer.
According to Behlau et al. fundamental frequency
is determined physiologically by the number of cycles that
the vocal folds make in a second, and they are the natural
result of the length of these structures.
Jitter and shimmer represent the variations that occur
in the fundamental frequency. Whereas jitter indicates the
variability or perturbation of fundamental frequency, shimmer
refers to the same perturbation, but it is related to amplitude of sound wave, or intensity of vocal emission. Jitter is
affected mainly because of lack of control of vocal fold
vibration and shimmer with reduction of glottic resistance
and mass lesions in the vocal folds, which are related with
presence of noise at emission and breathiness." [3]

[1] https://www.scielo.br/j/rboto/a/jfYLfsybBtsWkfrnS5ZHhNP/?format=pdf&lang=en

[2]https://nlp.lsi.upc.edu/papers/far_jit_07.pdf

[3]http://anlage.umd.edu/Microwave%20Measurements%20for%20Personal%20Web%20Site/Tek%20Intro%20to%20Jitter%2061W_18897_1.pdf


__Note:__ _As a result of my research and visualizations on the dataset, it seems that a single value in the Pitch Lo0cal Perturbation Measures values and Amplitude Perturbation Measures Values groups can represent this group. And this value is Jitter_rel( Jitter Relative) value according to the following visualizations.
So I'm thinking of eliminate the data inside this set of values._


__HNR Values:__

Harmonic noise ratio (Harmonic-to-Noise Ratio, HNR): It is the ratio of the total of the fundamental frequency and its multiples of harmonics to the noise. Its unit is dB, and high values indicate that the ratio of sound to noise is low. This parameter, which was not measured by MDVP,  it can be measured with Praat and Dr. Speech Vocal Assessment (Tiger DRS, Ine.).

"Harmonic to Noise Ratio (HNR) measures the ratio between periodic and non-periodic components of a speech sound. It has become more and more important in the vocal acoustic analysis to diagnose pathologic voices. The measure of this parameter can be done with Praat software that is commonly accept by the scientific community has an accurate measure." [4]

These variables, which called ratio variables, have higher numbers compared to other variables. So I can do a standardization process.

[4]https://www.sciencedirect.com/science/article/pii/S1877050918316739#:~:text=measures%20the%20ratio,an%20accurate%20measure.

__MFCC Values:__ 

_Mel frequency cepstral coefficient_

Mel-frequency cepstrum[5][6] coefficents, known as MFCC for short, is a fourier based transformation[7] used in feature extraction in applications such as speech recognition and speaker recognition. In short, it allows us to extract some information from the audio data that will characterize that audio data.

Variables named MFCC0, MFCC1,..., MFCC12 were recorded as a result of the measurement of the subjects voices from 0 to 12. So it looks like I will have to do a new operation on these variables.

[5] https://en.wikipedia.org/wiki/Mel-frequency_cepstrum

[6] https://en.wikipedia.org/wiki/Mel_scale

[7] https://en.wikipedia.org/wiki/Fourier_transform

__Delta Values:__

Delta variables (named Delta0, Delta1,..., Delta12) are derivatives of MFCC Values. I will probably do same operations to this variable group as I would do to the MFCC.


__DFA Value:__

"In stochastic processes, chaos theory and time series analysis, detrended fluctuation analysis (DFA) is a method for determining the statistical self-affinity of a signal. It is useful for analysing time series that appear to be long-memory processes (diverging correlation time, e.g. power-law decaying autocorrelation function) or 1/f noise.

The obtained exponent is similar to the Hurst exponent, except that DFA may also be applied to signals whose underlying statistics (such as mean and variance) or dynamics are non-stationary (changing with time). It is related to measures based upon spectral techniques such as autocorrelation and Fourier transform.

Peng et al. introduced DFA in 1994 in a paper that has been cited over 3,000 times as of 2020 and represents an extension of the (ordinary) fluctuation analysis (FA), which is affected by non-stationarities." [8]

[8]https://en.wikipedia.org/wiki/Detrended_fluctuation_analysis

__RPDE:__

Recurrence period density entropy

"Recurrence period density entropy (RPDE) is a method, in the fields of dynamical systems, stochastic processes, and time series analysis, for determining the periodicity, or repetitiveness of a signal."[9]

[9]https://en.wikipedia.org/wiki/Recurrence_period_density_entropy

__PPE Value__:

_Pitch Period Entropy_

The new research below mentioned about a new measure of dysphonia, called Pitch Period Entropy (PPE),  as a new method for diagnosing people with Parkinson's.

As I understand, many voice recognition methods are used in the dataset. It seems I will have to build a model where I can determine which values work most efficiently together or separately.

"We present an assessment of the practical value of existing traditional and non-standard measures for discriminating healthy people from people with Parkinson's disease (PD) by detecting dysphonia. We introduce a new measure of dysphonia, Pitch Period Entropy (PPE), which is robust to many uncontrollable confounding effects including noisy acoustic environments and normal, healthy variations in voice frequency. We collected sustained phonations from 31 people, 23 with PD. We then selected 10 highly uncorrelated measures, and an exhaustive search of all possible combinations of these measures finds four that in combination lead to overall correct classification performance of 91.4%, using a kernel support vector machine. In conclusion, we find that non-standard methods in combination with traditional harmonics-to-noise ratios are best able to separate healthy from PD subjects. The selected non-standard methods are robust to many uncontrollable variations in acoustic environment and individual subjects, and are thus well-suited to telemonitoring applications."[10]

[10]https://www.researchgate.net/publication/50377363_Suitability_of_Dysphonia_Measurements_for_Telemonitoring_of_Parkinson's_Disease

 __GNE Value__:
 
 _Glottal-to-noise excitation ratio_
 
 As I understand from the explanation below, the GNR variable is a value formed by comparing the HNR and NNE sound measurements. I want to compare it with Status and Gender variables and see the results. However, I have doubts about its necessity in the model since the GNR value is derived from the HNR which is in the dataset and the NNE data which is hidden in the dataset. After all, I can eliminate one of the two values.

"In this article a new acoustic parameter for the objective description of voice quality is introduced. It is based on
the correlation coefficient for Hilbert envelopes of different frequency bands. The parameter indicates whether a
given voice signal originatesfrom vibrations of the vocal folds or from turbulent noise generated in the vocal tract
and is thus related to (but not a direct measure of) breathiness. Therefore it is named Glottal-to-Noise Excitation
Ratio (GNE Ratio). GNE is compared to HNR (Harmonics-to-NoiseRatio) and NNE (Normalized Noise Energy),
existing measures also sensitive to additive noise (turbulence). Experiments with artificial signals show that only
the GNE is almost independent of frequency modulation noise (jitter) and amplitude modulation noise (shimmer)."[11]

[11] https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.549.2511&rep=rep1&type=pdf#:~:text=The%20parameter%20indicates%20whether%20a,Excitation%20Ratio%20(GNE%20Ratio)

## Result

__It has been mentioned above that traditional machine learning methods cannot be used. However, a research on papers of Naranjo et al. concluded that Bayesian regression models were used.[12] In addition, as a result of litarature research, in the paper that titled "Gradient boosting for Parkinson's disease diagnosis from voice recordings", a study was conducted on this dataset and it was stated that they achieved the best results with LGB. [13]__

__Therefore, I would like to study on this data set myself and evaluated the results.__

__Results__: _Machine learning models such as Random Forest, Gradient Boosting Machine, XGBoost, CatBoost, Light GBM and Naive Bayes have been tried and the best result with 0.8472 is obtained with the CatBoost model._

[12] https://pubmed.ncbi.nlm.nih.gov/27209185/

[13] https://bmcmedinformdecismak.biomedcentral.com/articles/10.1186/s12911-020-01250-7
