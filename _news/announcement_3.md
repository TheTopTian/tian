---
layout: post
title: Start a new project about Auto GPT
date: 2023.04.01-0400
inline: false
related_posts: false
---

The Chat GPT is so famous recently and I am also waiting for the reply from the radiology doctors. I begin to help my supervisor about the new open source project: Auto GPT.

***
**Project task**: In the field of healthcare, providing effective and personalized treatments to patients is crucial for their well-being and recovery. However, the process of selecting the most appropriate treatment option can be complex and challenging for doctors, especially when dealing with complex medical cases. With the advancements in natural language processing and machine learning, automated language models such as AutoGPT can assist doctors in their decision-making process.

AutoGPT is a powerful language model that is designed to generate human-like responses to text prompts. Compared with ChatGPT can only use the trained-information, in the latest version, Auto GPT can search the Google itself and grab the information from website directly via the Google API. By leveraging its ability to understand the context and nuances of medical language, AutoGPT can help doctors in the assessment of a patient's condition and recommend the most suitable treatment option. With its high accuracy and efficiency, AutoGPT can significantly improve the quality of medical care and reduce the time and resources required for medical decision-making.

This project aims to develop a system that uses AutoGPT to assist doctors in making treatment decisions for their patients. By analyzing medical records and input from doctors, the system will generate personalized treatment plans for patients based on their individual conditions and medical history. The system will also allow doctors to interact with AutoGPT to refine and modify the treatment plans, ensuring that the final recommendation is accurate and in line with the doctor's professional judgement.

***

I am currently trying to use Auto GPT do some simple task:

> **For example**: Propose an exercising plan for my diabetes type II (weight 120 kg, height 1,65m). My current HbA1c value is 10.5%

> **The output**:
```python
{
    "aerobic_exercises": [
        "brisk walking",
        "swimming",
        "cycling",
        "dancing"
    ],
    "resistance_exercises": [
        "weight lifting",
        "yoga",
        "pilates",
        "bodyweight exercises"
    ]
}
```

As you can see, although autogpt has the ability to iterate the prompt by itself, it takes him a long time to think, but the final output is very short. I will try to find a better prompt to let him output a diagnosis and treatment sheet similar to the one from a real doctor.
