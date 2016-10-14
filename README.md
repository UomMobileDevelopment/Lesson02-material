# Lesson02-material
## Περιγραφή του 2ου μαθήματος

### Εισαγωγικά
Για να μπορέσετε να εκτελείτε τον κώδικα στο κινητό σας θα πρέπει να έχετε ενεργοποιήσει στο κινητό το USB Debugging
ΠΩΣ ΕΝΕΡΓΟΠΟΙΟΥΜΕ ΤΟ USB Debugging: https://www.youtube.com/watch?v=NtrrtkSentA


Στο 2ο μάθημα θα κατασκευάσουμε απο την αρχή μια εφαρμογή ανάγνωσης καιρικών συνθηκών σε λίστα.

![alt tag](https://github.com/UomMobileDevelopment/Lesson02-material/blob/master/Shunshine-dummy-screen-smaller.png)


### Οδηγίες
- Ξεκινάμε σχεδιάζοντας το mockup σχέδιο της οθόνης μας. Πώς θέλουμε να εμφανίζονται οι καιρικές συνθήκες;

- ```MainActivity``` Η βασική κλάση απο την οποία ξεκινάνε όλα. Εκεί μέσα υπάρχει η inner class ```PlaceholderFragment```. Το Fragment είναι ένας αρθρωτός γραφικός υποδοχέας που μπορεί να επαναχρησιμοποιηθεί σε άλλα Activities. (modular container).

- Η λίστα με τις ημέρες πρόγνωσης θα υλοποιηθεί με τη βοήθεια του ```ListView```. Κάθε ```ListView``` γεμίζει πολλά ```ListItems```. Γιαυτό πρέπει να ορίσουμε το πώς θα φαίνεται το list item.

- Προσθέτουμε στον φάκελο res/layout to αρχείο ```list_item_forecast.xml``` (res->layout-> right click-> New -> Layout Resource file ) 
Το αρχείο περιγράφει ένα TextView (μόνο, τίποτε άλλο) με ID ```@+id/list_item_forecast_textview```. Συνολικά το αρχείο πρέπει να έχει:

```
<?xml version="1.0" encoding="utf-8"?>
<TextView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:minHeight="?android:attr/listPreferredItemHeight"
    android:gravity="center_vertical"
    android:id="@+id/list_item_forecast_textview">
</TextView>
```
Δίνουμε προσοχή στα:
```
android:layout_height="wrap_content"
android:minHeight="?android:attr/listPreferredItemHeight"
android:gravity="center_vertical"
```

-Εισαγωγή στο Responsive design. Γιατί είναι σημαντικό; (γιατί έχουμε πολλά και διάφορα μεγέθη οθονών και συσκευών).
-Τρόπος σκέψης. Να δούμε παραδείγματα (http://rollpark.us/, https://www.wired.com/ http://www.theatlantic.com/world/ )
-Layout Managers. Κυριότεροι: Frame Layout, Linear Layout, Relative Layout
-Frame: ιδανικό για απλές περιπτώσης όπου στην οθόνη έχουμε μόνο ένα συστατικό, όπως πχ μια λίστα
-Linear: ιδανικό για στίβαγμα συστατικων το ένα δίπλα στο άλλο ή το ένα κάτω απο το άλλο. Μας βοηθά επίσης να χωρίσουμε την οθόνη σε μέρη.
-Relative: δυνατό αλλα πολύπλοκο. Εδώ ορίζουμε τη διάταξη του κάθε συστατικού *σε σχέση* με κάποιο άλλο συστατικό
-
