# Android MVP

### What is MVP
It is an architecture that provides code reusability and testability. MVP application can be divided into three parts

![Android MVC](android/android-mvp-concept-diagram.JPG)

* Model
    * DataManager
        * ApiHelper
        * DatabaseHelper
        * PrefHelper
* View
    * Activity
    * Fragment
* Presenter
    * Each view has a presenter.
    * A Presenter is used to generate Views and bind Objects to them on demand.

