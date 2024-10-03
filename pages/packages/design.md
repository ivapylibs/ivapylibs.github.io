@page design Software Design Principles



## Image and Visual Processing as Estimation

Given that much of computer vision relates to signal processing or requires functionality
that behaves like an estimator, a good portion of the visual processing code is designed
with an interface resembling that of a filter.  It has prediction, measurement,
correction, and adaption steps. For the most basic version, much of these steps are no-ops
and only the measurement implements the processing.  The next step up includes correction
with static prediction (e.g., still a prediction no-op).  After that, more complex
approaches include non-static prediction models or adaptation.  Adaptation is
tricky, but generally applies to the parameters or models used for prediction or
processing.  Based on collected data, the models can be adjusted to factor for (slowly)
changing visual conditions or slightly incorrect initial models.  This design philosophy
arises from the implicit connection that many computer vision algorithms have with the field
of control theory, in particular estimation theory. Cameras are, after all, sensors that
provide implicit measurements of the world, from which the signal of interest must be
recovered.

As computer vision approaches evolve and computer performance improves, the algorithms
tend to transition to fixed-window smoothers.  The software design paradigm permits use of
a smoother implementation within the estimation-based interface.
Interestingly, the computer vision community tends to implement the smoothers as zero-lag
smoothers, which are better than standard filters but don't benefit from two-sided
information thus the improvements in estimation accuracy is not as much as one would
expect.  A more robust implementation is as a fixed-lag smoother, which taps the state
signal from the interior portion of the smoothing window.  Accuracy improves due to having
information before and after the tapped time point, however there is a delay in signal
availability.  If such a delay is tolerable, then fixed-lag methods will outperform
zero-lag methods. If post-processing is possible, then a well-designed global optimization
will provide the best estimates.

As a final note, even though the underlying implementation derives from a filter-based
interface, the API includes a single invocation option (called ``process``). It is common
for this method to be invoked, which will then sequentially call the different steps and
store the intermediate results. The API permits access to the final result and the
intermediate ones.
