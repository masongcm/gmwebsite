+++
# Date this page was created.
date = 2018-08-28T12:00:00

# Project title.
title = "The Effects of a Pregnancy Intervention in Finland"

# Project summary to display on homepage.
summary = "Can a lifestyle intervention during pregnancy improve the lives of overweight mothers and their offspring?"

# Optional image to display on homepage (relative to `static/img/` folder).
image_preview = "radiel.jpg"

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["Small Sample", "Experiments", "Multiple Hypotheses", "Permutation Inference", "DynaHEALTH", "Ongoing"]

# Optional external URL for project (replaces project detail page).
external_link = ""

# Does the project detail page use math formatting?
math = false

# Featured image
# To use, add an image named `featured.jpg/png` to your project's folder. 
[image]
  # Caption (optional)
  caption = "Photo by [Heather Mount](https://unsplash.com/@heathermount) on [Unsplash](https://unsplash.com)"
  
  # Focal point (optional)
  # Options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
  focal_point = "Center"

# Optional featured image (relative to `static/img/` folder).
[header]
image = "headers/radiel-wide.jpg"
caption = "Photo by [Heather Mount](https://unsplash.com/@heathermount) on [Unsplash](https://unsplash.com)"

+++

Can we improve pregnancy outcomes by simply encouraging and supporting mothers to adopt a healthy lifestyle during pregnancy? This is the question the Finnish Gestational Diabetes Prevention Study (RADIEL) sets out to answer. 

More than 250 mothers were selected among high-risk women, that is with high BMI and previous gestational diabetes. They were randomly assigned to receiving counselling during their pregnancy, with the aim of limiting weight gain by exercising and eating a healthier diet. 

The RADIEL team in Finland recently published the results on leading international journals -- see [Koivusalo et al. (2016)](http://care.diabetesjournals.org/content/39/1/24.long). As part of the [DynaHEALTH](https://www.dynahealth.eu) project, I was kindly granted access to the data collected by the Finnish team, together with my PhD supervisor Gabriella Conti. We want to re-evaluate the effect of the experimental intervention on a wider range of outcomes, including the mother's post-pregnancy weight, mental health, and self-rated health. In particular, we wanted to know if the effect of the intervention was different for higher-risk mothers. 

We need to take some important methodological issues into account:

1. **Issue**: The sample is relatively _small_, especially if we want to investigate effects in subsamples. **Solution**: We use _resampling techniques_ to perform inference that is a valid approximation in the finite sample. This also accounts for the strata used in the randomisation process, by randomising within blocks.

2. **Issue**: The sample might be _imbalanced_ with respect to some pre-randomisation characteristics. **Solution**: We implement a _linear conditioning_ approach to account for baseline differences.

3. **Issue**: There is a relevant amount of _attrition_, i.e. mothers dropping out of the study. Some of it is non-random -- for example younger mothers are more likely to leave. **Solution**: We reweight the analysis using _inverse-probability weights_, so that mothers with characteristic more similar to the ones who dropped out of the study are given more weight.

4. **Issue**: Testing _many hypotheses_ at a time, you're bound to "stumble" on something that is statistically significant. Technically, one in twenty of your null hypotheses are guaranteed to be rejected by pure chance even in absence of any real effect. **Solution**: we programmed a state-of-the-art _stepdown adjustment_ to our p-values, that takes into account the multiplicity of hypotheses and avoids p-hacking.

All of the above is neatly packaged in a Stata routine, which is now being tested. Hopefully I'll have some time to translate this into R, which would make it more accessible!

Results will be submitted for publication soon. Stay tuned!


**BONUS**: Hear me talk about our results on Vimeo!
{{< vimeo 271691834 >}}


