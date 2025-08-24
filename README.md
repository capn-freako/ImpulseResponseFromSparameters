# ImpulseResponseFromSparameters

A comparison of different techniques (i.e. - windowing, vector fitting, etc.) for extracting the impulse response from S-parameters.

## Introduction & General Intent

On August 25, 2020 I had an article published in Signal Integrity Journal (SIJ) titled, _Impulse Response from Insertion Loss_.
In my article I explained how the raw, positive frequency only, data contained in a Touchstone® file needed to be conjugate duplicated and reordered, in order to get a correct impulse response from a typical `ifft()` function.
I also went on to explain how applying windowing to the data, before calling `ifft()`, can help eliminate the non-causal ringing, which typically occurs as a result of the incomplete data in most Touchstone files.

Later, on May 12, 2022, Professors Morales and Agili, of Penn State Harrisburg's _Center for Signal Integrity_, presented a SIJ webinar titled, _The Use of DSP Techniques to Analyze S-Parameter Sampled Data_.
Their webinar was partly a rebuttal to my own previous article.
In fact, they used some of my figures unaltered, presumably to make it quite clear that they were rebutting my suggestion of the use of windowing techniques to smooth non-causal ringing.
In their webinar, they propose, as an alternative to windowing, the use of certain DSP techniques, in particular the [_Bilinear Transform_](https://en.wikipedia.org/wiki/Bilinear_transform), to better transform the raw frequency domain S-parameter data in a Touchstone file into the _discrete_ time domain, for further processing there.

I responded, on January 16, 2023, with a _Jupyter_ notebook published as a Gist, which partially rebutted Morales and Agili's critique of my original article and pointed out some flaws in their understanding of certain relevant concepts.
Professor Morales was kind enough to take the time to respond, in the form of a comment on this Gist.
I then posted a notification of that fact to the _SI List_ e-mail reflector, inviting others to join in the discussion.
Since then several other individuals have contacted me about this topic, expressing interest in participating in the debate but unsure of how best to do so.
So, I created this new Github repository, to provide a central and well organized platform for that discussion.
The intent of this repo. is twofold:

1. To foster focused discussion by topic of:

	- [my original SIJ article](https://www.signalintegrityjournal.com/articles/1847-impulse-response-from-insertion-loss),
	- [the SIJ webinar rebutting my article, by Prof. Morales & Agili](https://www.signalintegrityjournal.com/ext/resources/Media-Kit-2022/DrAldoMorales_The-Use-of-DSP-Techniques-to-Analyze-S-Parameter-Sampled-Data_2022.pdf),
	- [my Gist critiquing some of the reasoning behind their rebuttal](https://gist.github.com/capn-freako/782135b2914662c6c1fc40b9256f251f), and
	- [Professor Morales' comments on that Gist](https://gist.github.com/capn-freako/782135b2914662c6c1fc40b9256f251f?permalink_comment_id=5178891#gistcomment-5178891). (Scroll to bottom if not initially visible.)
		- **Note:** Please, do _not_ add to this commentary, but instead use an _Issue_ in this new repo. to further discussion.
		And, please, try to keep a 1:1 relationship between _Issues_ and discussion topics.
		That will keep the various topics being debated well separated and assist new participants in acclimating quickly.

2. To provide a central public space for developing our communal understanding of the pros & cons of the various techniques available for extracting the _impulse response_ from the S-parameters:

	- Inverse Fourier transforming, with and without pre-windowing,
	- Vector fitting, using the _Bilinear Transform_,
	- others?
