## Introduction:

This API is designed to predict tomato diseases based on input images. The aim is to aid in the early detection of diseases in tomato plants to improve crop yield and reduce losses.

## Technologies Used:

### Frameworks and Libraries:
- Flask: Used as the web framework to create the API endpoints.
- Keras: Deep learning framework used for building and training the convolutional neural network (CNN).
- BeautifulSoup: Library used for web scraping to extract treatment information.

### Data Handling:
- NumPy: Used for numerical computations on image data.
- ImageDataGenerator (from Keras): Used for data augmentation and preprocessing of input images.
- OpenCV: Used for image processing tasks such as resizing and normalization.

### Dataset
- The model was trained on a dataset containing images of various tomato diseases. The dataset used for training is not included in this repository.cuase its big over 7gb .it contains over 10000 images

## Model Architecture:

The CNN model architecture consists of:
- Two convolutional layers with ReLU activation.
- Two max-pooling layers for down-sampling.
- One fully connected hidden layer with ReLU activation and dropout regularization.
- One output layer with softmax activation for multi-class classification.
- The model has about `25,768 paramters`
- The acuracy is `86.6%` which will be futher improved if  more data or a larger dataset were available</s> 
## Data Preparation:

The training and validation data are preprocessed using the ImageDataGenerator from Keras:
- Rescaling: Images are rescaled to a range of [0, 1].
- Data Augmentation: Shearing, zooming, and horizontal flipping are applied to increase the diversity of training samples.

## Training Process:

The model is trained using the training dataset generated by the ImageDataGenerator.
- The Adam optimizer is used with categorical cross-entropy loss.
- The training process consists of 1000 epochs with a batch size of 64.

## Evaluation:

The model's performance is evaluated on the validation dataset using the evaluate_generator function from Keras.
- The accuracy metric is used to assess the model's performance.

## Deployment:

The API is deployed using Flask.
- The `/predict` endpoint accepts POST requests with image files and returns predictions along with treatment information.
- The treatment information is obtained through web scraping using BeautifulSoup from Google search results.

Response Format:

```json 

{
    "prediction": "Disease Name",
    "message": "saved successfuly to db",
    "result": [
        {
            "url": "Treatment URL",
            "title": "Treatment Title",
            "content": "Treatment Content (TEXT)"
        },
    
    ]
}
```
## How it works?

- **Upload Image**: Users create an account and upload an image of a tomato to the platform.
  
- **Image Classification**: The AI system analyzes the uploaded image using a trained model to classify the tomato into one of several possible diseases. This classification is based on patterns and features extracted from the image.

- **Treatment Recommendations**: After classifying the tomato disease, the system is able to search through the internet or online resources to gather relevant information about the detected disease. It then provides users with recommended treatments or management strategies sourced from credible online sources.

- **User Feedback and Improvement**: Users can provide feedback on the accuracy of the classification and the usefulness of the provided treatment recommendations. This feedback loop helps improve the AI model's performance over time, leading to more accurate classifications and better treatment suggestions.


## Future Improvements:

- Improved model architecture: Experiment with deeper CNN architectures or transfer learning approaches.
- Enhance treatment information extraction: Explore more robust methods for extracting relevant treatment information from search results.
- Scalability: Implement scalability features to handle larger volumes of prediction requests.

## Conclusion:

This API provides a valuable tool for farmers and agricultural professionals to identify and mitigate tomato plant diseases early, contributing to improved crop yield and food security.
- Further enhancements and optimizations can be made to improve the accuracy and usability of the API.

This project is licensed under the MIT License - see the [LICENSE](https://github.com/glennin-codes/TomatoeDeseaseDetector/blob/main/LICENSE) file for details.