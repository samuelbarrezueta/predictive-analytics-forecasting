# Pedro – Presentation Script (1 minute)

## Slide 20 – Model 1: Gradient Boosting (tree ensemble)

Our first model is **gradient boosting**, a tree ensemble. Fatal crashes come from combinations, like rural, at night, on a downhill, and trees learn those combinations by themselves. We tuned it on the 2022–23 validation years only.

On the test set, it reaches **31.5% of fatal crashes with just 15% of ALS capacity**: **2.1 times better than random**. The main drivers are time of day, roadway type and historical segment risk, as in our EDA.

**→ NEXT SLIDE**

## Slide 21 – Model 2: MLP neural network (non-tree)

Then we asked: is the limit the algorithm, or the data? So we tried a very different model, a **bag of five neural networks**. It reaches **31.2%**, almost the same.

As you can see, the curves of all the models almost overlap. With only road, place and time at the moment of the call, **the data is the limit, not the algorithm**.
