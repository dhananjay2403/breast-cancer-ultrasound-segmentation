# Project Workflow Summary

## Initial Approach

- **Architecture:**  
  Implemented a standard U-Net for semantic segmentation.
- **Preprocessing:**  
  - Converted images to grayscale and **initially resized to 128x128** for faster experimentation.
  - Normalized pixel values to [0, 1].
  - Combined multiple ground truth masks per image.
- **Training:**  
  - Used default Keras loss (not segmentation-specific).
  - Did **not specify any learning rate** at first (used Keras defaults).
  - Early stopping on validation loss.

- **Initial Results:**  
  - Validation accuracy: **~0.88**  
  - Mean IoU: **~0.60**  
  - IoU (Jaccard): **~0.50**  
  *(Started with much lower accuracy and IoU; model was underfitting and not generalizing well.)*

---

## Improvements & Iterations

- **Switched to Segmentation-Specific Losses:**  
  Introduced **Dice Loss** and **Binary Crossentropy + Dice Loss** for better segmentation performance.

- **Learning Rate Tuning:**  
  - Set learning rate to **1e-4** for more stable training.
  - Later increased to **2e-4** for faster convergence and improved results.

- **Increased Image Size:**  
  Switched from 128x128 to **256x256** images for better segmentation detail and accuracy.

- **Made U-Net Deeper:**  
  Added extra encoder/decoder blocks and increased filters.  
  *Result: No significant improvement; metrics plateaued.*

- **Added Dropout Regularization:**  
  Inserted Dropout layers after pooling and convolutional layers.  
  *Helped reduce overfitting.*

- **Introduced Data Augmentation:**  
  Used mild augmentations (rotation, shift, zoom, horizontal flip) via Keras’ `ImageDataGenerator`.  
  *Improved generalization and validation metrics.*

- **Hyperparameter Tuning:**  
  Experimented with batch size and learning rate.  
  Used early stopping to avoid overfitting.

---

## Final Model & Results

- **Architecture:**  
  Deep U-Net with Dropout and data augmentation.
- **Loss Function:**  
  Combined Binary Crossentropy and Dice Loss.
- **Learning Rate:**  
  Final value: **2e-4**
- **Metrics Achieved:**  
  - Validation Accuracy: **~0.96**  
  - Validation Loss: **~0.40**  
  - IoU (Jaccard): **~0.66**  
  - Mean IoU: **~0.81** (considered strong for medical segmentation)

---

## Key Learnings & Decisions

- Starting with smaller images (128x128) was useful for rapid prototyping; increasing to 256x256 improved results.
- Switching to segmentation-specific loss functions (Dice, BCE+Dice) was crucial for boosting performance.
- Careful learning rate tuning (from default to 1e-4, then 2e-4) improved convergence and final metrics.
- Making the model deeper alone did not improve results; regularization and data augmentation were crucial.
- Mild data augmentation is important for medical images to avoid unrealistic transformations.
- Dropout helped reduce overfitting and improved generalization.
- Careful monitoring of metrics and iterative tuning led to significant improvements.