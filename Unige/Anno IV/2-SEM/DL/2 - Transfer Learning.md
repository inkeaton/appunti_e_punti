+ **Transfer learning** is a technique used to help the training of a model when we have **few data available**
+ The idea is simple:
	+ We assume to have another model already trained on a sufficient amount of data
	+ We decide to keep part of this model and modify the remaining, in order to adapt it to the required task
+ The two main approaches we saw were:
	+ **Feature Extraction**: We "freeze" the extraction part of the model, not training it anymore, and we attach a classifier, which will be trained for our task
	+ **Fine-Tuning**: Similar to before, but we allow parts of the model to be trained
+ Deciding which approach to use highly depends on the data in our possess and how they relate to the pre-trained model (*details in slides*)
+ Another approach is **Knowledge Distillation**:
	+ Given a pre-trained model, we train a smaller one in order to mimic its feature extraction (Feature-based knowledge), its classifier (Response-based knowledge) or both (Relation-based knowledge)
	+ This gives us smaller and more efficient models, equivalent to the original, but less prone to overfitting and similar