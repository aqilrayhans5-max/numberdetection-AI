# DigitLab — MNIST Handwritten Digit Recognition

A static browser-based web page where visitors can either draw a digit or upload an image containing one handwritten digit (0–9). It returns a prediction and probability scores without a Python backend, Node.js server, or local development server.

## Publish it online (GitHub Pages)

1. Sign in to GitHub and create a new repository, for example `mnist-digit-web`.
2. Extract this ZIP on your computer. Upload `index.html` and `README.md` to the root of your new repository using **Add file → Upload files** on GitHub.
3. Open **Settings → Pages** in the repository.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Choose the `main` branch and `/ (root)` folder, then click **Save**.
6. After GitHub Pages publishes it, the page URL will appear in the same Pages section. It will usually look like `https://YOUR-USERNAME.github.io/mnist-digit-web/`.

You do not need to run any commands or start a server locally. You only use your browser to upload the files and enable hosting.

## How it works

- HTML, CSS and JavaScript make the responsive interface and drawing canvas.
- TensorFlow.js runs the CNN in the visitor's browser.
- The page supports drawing or uploading a PNG, JPG, or WEBP image.
- Uploaded images are converted to high-contrast black-on-white, cropped around the detected foreground, centered and scaled before being converted into the 28 × 28 MNIST input.
- The page predicts a digit from 0 to 9 and shows the scores for all ten classes.

## Important limitations

This MNIST model is a **single-digit classifier**. Upload an image with one clear handwritten digit, ideally on a plain background. A picture containing a full multi-digit number is not automatically split into its individual digits in this version. For that, a digit-segmentation or OCR feature would be needed. Photo shadows, decorative fonts, rotated digits, and low contrast can affect accuracy.

The page downloads pretrained weights from the public repository [PHOX-9/Digit-Recognition](https://github.com/PHOX-9/Digit-Recognition). The model weights are not included in this ZIP. Therefore, visitors need an internet connection, and the model depends on that public URL continuing to be available. For a long-lived or production deployment, replace `WEIGHTS_URL` in `index.html` with the URL of a model you trained and are authorized to host.

The displayed confidence is the model's score, not a guarantee that the prediction is correct.
