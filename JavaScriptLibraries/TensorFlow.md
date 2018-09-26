# Tensorflow

Tensor flow is a machine learning library. The offical documentation can be found here <a href="https://www.npmjs.com/package/@tensorflow/tfjs">https://www.npmjs.com/package/@tensorflow/tfjs</a>

An example of tensor flow in a cell

```JavaScript
const tf = tensorFlowjs;

// Define a model for linear regression.
const model = tf.sequential();
model.add(tf.layers.dense({units: 1, inputShape: [1]}));

// Prepare the model for training: Specify the loss and the optimizer.
model.compile({loss: 'meanSquaredError', optimizer: 'sgd'});

// Generate some synthetic data for training.
const xs = tf.tensor2d([1, 2, 3, 4], [4, 1]);
const ys = tf.tensor2d([1, 3, 5, 7], [4, 1]);

inputs[0].forEach((i) => {
   i;
});

// Train the model using the data.
model.fit(xs, ys, {epochs: 10}).then(() => {
    // Use the model to do inference on a data point the model hasn't seen before:
    // Open the browser devtools to see the output
    return tf.tensor2d([5], [1, 1]).toString();
});
```
