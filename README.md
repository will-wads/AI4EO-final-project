# AI4EO-final-project

Cloud Coverage Classification Using CNN and Sentinel-2 Data
Project Overview
This project is based on the classification of cloud coverage using satellite imagery, specifically data from Sentinel-2. The goal is to accurately detect the presence and extent of clouds in imagery using deep learning, namely Convolutional Neural Networks (CNNs). This task is increasingly critical in remote sensing applications, as cloud contamination can severely affect the quality and usability of satellite data.
The notebook implements a supervised learning approach where cloud masks were manually generated using IRIS and then used as training labels for a CNN. The final model was tested on unseen regions to assess generalisation.
For more detailed instructions and configuration options on setting up IRIS yourself, please refer to the IRIS GitHub repository.


Why Quick Cloud Coverage Detection is Useful
Image usability filtering: Quickly discarding cloud-heavy images saves time and processing in downstream tasks such as land use classification, vegetation monitoring, or surface temperature retrieval.
Preprocessing in large pipelines: In operational satellite systems, identifying unusable imagery before further analysis improves accuracy.
Climate monitoring: Helps improve cloud cover statistics and support models in atmospheric research.
Why Use CNN for This Task?
A Convolutional Neural Network (CNN) is a type of deep learning model specifically designed for processing image data. Unlike traditional neural networks, CNNs use layers called convolutional layers that apply filters (or kernels) across an image to detect patterns such as edges, shapes, textures, and other spatial features.
This makes CNNs particularly well-suited for image classification tasks like cloud detection in satellite imagery, where spatial relationships and patterns are key. By stacking multiple convolutional layers, the model can learn increasingly complex visual features — starting from basic edges to full cloud formations — allowing it to distinguish between cloudy and non-cloudy areas with high accuracy.
CNNs are powerful because they:
Learn directly from raw image data.


Preserve spatial structure (unlike fully connected layers).


Are translation-invariant — meaning they recognize features anywhere in the image.


Workflow Summary
Data Acquisition: Satellite data was acquired from Copernicus Open Access Hub using Sentinel-2 imagery.
Manual Masking: IRIS was used to label cloud regions in selected images.
Preprocessing: RGB bands (B04, B03, B02) were extracted, resized, and normalised.
Model Architecture: A lightweight CNN was designed using TensorFlow/Keras.
Training & Evaluation: The model was trained on labelled data and validated on a geographically distinct region.
Full Image Rollout: The trained model was applied to a full-resolution image to assess performance.


Dependencies
TensorFlow
NumPy
Matplotlib
Scikit-image
netCDF4 (for Sentinel-3 support if extended)

Results
The CNN achieved strong visual correspondence between predicted cloud masks and manually labelled ground truth.
Full-image inference worked effectively when normalisation and patch reassembly were handled correctly.

Environmental Impact Assessment
This project was executed using Google Colab, which operates on Google Cloud’s energy-efficient infrastructure. The environmental impact of running the notebook was estimated using publicly available data on energy consumption, water usage, and carbon emissions associated with cloud computing.
Energy Usage
Although exact energy usage depends on the backend assigned (CPU, GPU, or TPU), a typical Colab session running a lightweight Convolutional Neural Network (CNN) for training and inference is estimated to consume approximately:
Estimated energy consumption: 0.05–0.15 kWh
This estimate is based on the following assumptions:
Power draw of 100–300 W during computation


Execution time of 30–60 minutes


Data center overhead represented by a Power Usage Effectiveness (PUE) of approximately 1.1–1.2 (Google, 2021)


These assumptions follow methodologies suggested in:
Strubell et al. (2019)


Henderson et al. (2020)


Note: These sources do not provide direct energy values for CNN inference. The estimate above is inferred based on typical cloud hardware performance and session duration.

Water Consumption
According to Google’s 2021 Environmental Report, the company consumed 12.5 billion litres of water while using approximately 18 terawatt-hours (TWh) of electricity, resulting in a Water Usage Effectiveness (WUE) of:
WUE: ~0.69 litres per kilowatt-hour (kWh)
Applying this to the estimated energy usage of the notebook session:
Estimated water use: 3.5–10.5 litres
This estimate reflects water used primarily for evaporative cooling in data centres (Google, 2021).

Carbon Emissions
Assuming a global average carbon intensity of electricity ranging from 300 to 600 grams of CO₂-equivalent per kWh, the estimated emissions associated with this session are:
Estimated CO₂ emissions: 15–90 grams of CO₂e
Although Google Cloud aims to match energy usage with renewable energy, actual emissions may vary based on regional infrastructure and time-of-day factors (Ritchie and Roser, 2020).

References
Google (2021) Google Environmental Report 2021. Available at: https://www.gstatic.com/gumdrop/sustainability/google-2021-environmental-report.pdf (Accessed: 29 May 2025).


Henderson, P., Hu, J., Romoff, J., Brunskill, E., Jurafsky, D. and Pineau, J. (2020) ‘Towards the systematic reporting of the energy and carbon footprints of machine learning’, arXiv preprint, arXiv:2002.05651. Available at: https://arxiv.org/abs/2002.05651 (Accessed: 29 May 2025).


IRIS (no date) IRIS – Intelligently Reinforced Image Segmentation. European Space Agency PhiLab. Available at: https://github.com/ESA-PhiLab/iris (Accessed: 29 May 2025).


Masanet, E., Shehabi, A., Lei, N., Smith, S. and Koomey, J. (2020) ‘Recalibrating global data center energy use estimates’, Science, 367(6481), pp. 984–986. DOI: 10.1126/science.aba3758.


Our World in Data (2022) Carbon intensity of electricity. Available at: https://ourworldindata.org/grapher/carbon-intensity-electricity (Accessed: 29 May 2025).


Strubell, E., Ganesh, A. and McCallum, A. (2019) ‘Energy and policy considerations for deep learning in NLP’, in Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics, pp. 3645–3650. Available at: https://arxiv.org/abs/1906.02243 (Accessed: 29 May 2025).

