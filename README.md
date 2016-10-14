# Lesson02-material
περιγραφή του 2ου μαθήματος

Για να μπορέσετε να εκτελείτε τον κώδικα στο κινητό σας θα πρέπει να έχετε ενεργοποιήσει στο κινητό το USB Debugging
ΠΩΣ ΕΝΕΡΓΟΠΟΙΟΥΜΕ ΤΟ USB Debugging: https://www.youtube.com/watch?v=NtrrtkSentA


Στο 2ο μάθημα θα κατασκευάσουμε απο την αρχή μια εφαρμογή ανάγνωσης καιρικών συνθηκών σε λίστα.

![alt tag](https://github.com/UomMobileDevelopment/Lesson02-material/blob/master/Shunshine-dummy-screen-smaller.png)


##Εισαγωγή
- Ξεκινάμε σχεδιάζοντας το mockup σχέδιο της οθόνης μας. Πώς θέλουμε να εμφανίζονται οι καιρικές συνθήκες;

- ```MainActivity``` Η βασική κλάση απο την οποία ξεκινάνε όλα. Εκεί μέσα υπάρχει η inner class ```PlaceholderFragment```. Το Fragment είναι ένας αρθρωτός γραφικός υποδοχέας που μπορεί να επαναχρησιμοποιηθεί σε άλλα Activities. (modular container).

- Η λίστα με τις ημέρες πρόγνωσης θα υλοποιηθεί με τη βοήθεια του ```ListView```. Κάθε ```ListView``` γεμίζει πολλά ```ListItems```. Γιαυτό πρέπει να ορίσουμε το πώς θα φαίνεται το list item.

- Προσθέτουμε στον φάκελο res/layout to αρχείο ```list_item_forecast.xml```. res->layout-> right click-> New -> Layout Resource file  
