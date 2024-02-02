# Object-tracking-hungarian-algorithm
Hungarian algorithm in Python (not optimized) used in simple object-tracking task (comparing two frames of a single video).

Hungarian algorithm is an optimization algorithm used to solve the assignment problem like: "Worker A completes task X in M minutes and task Y in N minutes; worker B completes task X in R minutes and task Y in P minutes. What is the best way to assign tasks so the work is completed the fastest way possible?". You can learn about Hungarian algorithm, for example, here: https://www.columbia.edu/~cs2035/courses/ieor6614.S16/GolinAssignmentNotes.pdf 

The first example use that came to my mind was object-tracking, and for the sake of clarity, I've taken 2 frames of a single video. Solution of this problem consists of 3 main parts:
  - Detecting objects on each frame using YOLO (v8) detection system.
  - Creating correspondence matrix that for each element of first and second frames (therefore its' shape is MxN, not always NxN) [i][j] shows intersection area of i-th and j-th objects.
  - That correspondence matrix is used as an input for Hungarian algorithm. It outputs matching matrix of shape Gx2, where G = max(N,M). This matrix is later used to rearrange ids of objects in second frame.
