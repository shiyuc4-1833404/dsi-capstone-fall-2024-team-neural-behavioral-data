[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/m5cwIV43)
# Data Science Capstone & Ethics (ENGI E4800)

## Course overview

This course provides a unique opportunity for students in the MS in Data Science program to apply their knowledge of the foundations, theory and methods of data science to address data driven problems in industry, research, government and the non-profit sector. The course activities focus on a semester-long project sponsored by an affiliate company or a Columbia faculty member. The project synthesizes the statistical, computational, engineering and social challenges involved in solving complex real-world problems. The course has a well developed Ethics component supported by Dr. Savannah Thais. 

## Team Structure

Select a team captain (with or without help from mentor/instructor/supervisor)

Record your names here in this format-
1. Ailu Yu, ay2607
2. Eva Zhang, yz4214
3. Shiyun Chen, sc5324
4. Fei Du, fd2547
5. Zoey Li, zl3360
6. Chanjin Park, cp3366

## Instructions

The CourseInfoForStudents folder has the templates for your  reports, meeting minutes with your mentors and check-in questions with your support team. These are the deliverables you need to save as .pdf files and upload in this repository. Additionally the folder also contains sample meeting presentations and tips, report grading rubrics, student-mentor email templates and syllabus for your reference.

## Main Deliverables

1. Code
2. Reports- Midterm Progress Report, Final Report, Ethics Report
3. Weekly Check-ins (progress questions)

For No.3- refer to the course info and maintain a weekly log of all within the folders named according to the name of the deliverables. Please fill up 1-2 sentence answers for each question (present in the document within CourseInfo labeled Key Questions for Check-Ins.txt) for each week and place it as Week 1, Week 2, .. and so on within a new folder in the repo named Weekly Check-Ins. We will be referring to the answers you write before every check-in so we can help you better. 

NOTE: Completion of weekly check in progress logs and showing up for the 15 minute check ins will count towards your participation grade.

The code can be placed in a folder named code, and the remaining files can be placed as .pdf files in the root directory.

## Progress Documentation (Update Oct 13th)

In the kickoff meeting we have received general introduction regarding the experiment setting, dataset, and following steps regarding the whole project.

### Experiment Setting

The experiment records neural activity of mouse for food deprivation. 

The mouse are trained to dig pot to find reward under three variables - oder, texture, and direction.

The experiment lasts for 3 days.

- Day 1: Acquisition; follow oder 1
- Day 2: Reverse learning; follow oder 2
- Day 3: Set shifting; follow texture

### Dataset

- Neural data: different neuron activity at different phase of the experiment (time series)
- Cell activity: communicate through spikes, when a cell fires there is activity of neurons(1 for active, 0 for not active)
- Raw video: has been used to label different phase of the experiment

### Steps

1. Shape of video data to analyze across days (register different days)
   - Combine the neural data from different days into one data file
   - Neural data: Circular view of the brain of mouse in the experiment
   - Frame moving
   
2. Improve behavior annotation using machine learning techniques (annotate behaviors)
   - Getting data & information from the experiment videos:
      The phases of behaviors are collected by hand (watching videos), we may be able to find other ways to label these behaviors. For example, when some neurons are fired,        mice are digging, then there may be more details in the video, which can be collected through ML techniques.
   - Mars example experiments (neuroethology.github.io/MARS)

### Progress Oct 13th

We received videos of two mouse. Each video has two tiff files with 1000 frames each.

After receiving the data we've splited the tasks to:
1. Detecting changing point in videos
2. Image registration (including detecting shift and modifying the frames)

Our current progress are
1. We can detect the changing point by calculating correlation between frames and pick the point with maximum changing (given that we know there's only one changing point in each tiff file)
2. We've tried the cross-correlation, machine learning (with self-defined loss function), and mutual information method. It turns out that the mutual infromation method works well for detecting shifts between images. We will report our result to mentors to see if there's any further improvement needed. After mentors' verification we can start to modify all frames in a video. 

### Progress Oct 25th

Finish Phase 1 (Image Registration), including
1. Developed an alogirithm to detect frames with dramatic changes
2. Developed an algorithm based on mutual information to shfting offset images back to correct coordinates
3. Offering solutions with local optima and global optima for users' preferences

The algorithm is validated after using different representative frames as input images. It will be further evaluated by the lab using more data. 

The jupyter notebook including all codes and comments is uploaded with folder named "Phase_1".

### Progress Dec 4th

Finish and Wrap Up Phase 2 (Behavior Classification), including
1. Performed pose estimation to identify and extract the coordinates of specific body parts for each frame in the behavioral videos using DeepLabCut (DLC).
2. Annotated Mouse behavior manually and classified into four distinct categories: Others, Wandering, Investigating, and Digging.
3. Integrated step1 and step2 and developed an XGBoost (XGB) model to predict mouse behaviors on unseen data.

The model leverages pose-based features to classify behaviors for up to 87% accuracy, enabling automated behavior analysis.

The code notebook with comments and all necessary dataset are placed in the folder named "Phase_2".

### Next Step
1. Address Annotation Challenges:
   - Collaborate with the lab team to develop a clear rubric for behavior annotation, ensuring consistent and well-defined criteria for each behavior category.
   - Engage trained professionals or experienced team members to review and correct model-predicted annotations, creating a more accurate ground truth dataset.
2. Model Refinement:
   - Use the refined dataset with improved annotations to retrain the model, enhancing its performance, reliability, and alignment with precise behavioral definitions.
3. Data Integration:
   - Integrate behavioral data with neuroimaging data to uncover correlations between neural circuits and adaptive behaviors.
   - Explore mechanisms underlying cognitive flexibility through the combined analysis of behavioral and neuroimaging insights.
