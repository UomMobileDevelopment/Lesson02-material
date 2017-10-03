# Περιγραφή του 2ου μαθήματος

Παραδόσεις:

 - 15/10/16
 - 3/10/17


### Εισαγωγικά
Για να μπορέσετε να εκτελείτε τον κώδικα στο κινητό σας θα πρέπει να έχετε ενεργοποιήσει στο κινητό το USB Debugging
ΠΩΣ ΕΝΕΡΓΟΠΟΙΟΥΜΕ ΤΟ USB Debugging: https://www.youtube.com/watch?v=NtrrtkSentA


### Git Version Control System - Github online repository hosting

Σχετικό μάθημα για το Git https://classroom.udacity.com/courses/ud775

### Ξεκινάμε!

Μάθημα στο Udacity: https://classroom.udacity.com/courses/ud853/lessons/1395568821/concepts/15824886820923

Στο 2ο μάθημα θα ξεκινήσουμε την κατασεκυή απο την αρχή μια εφαρμογής ανάγνωσης καιρικών συνθηκών σε λίστα.

![alt tag](https://github.com/UomMobileDevelopment/Lesson02-material/blob/master/Shunshine-dummy-screen-smaller.png)




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

- Εισαγωγή στο Responsive design. Γιατί είναι σημαντικό; (γιατί έχουμε πολλά και διάφορα μεγέθη οθονών και συσκευών).
Τρόπος σκέψης για να χτίζω responsive layouts. Παραδείγματα (http://rollpark.us/, https://www.wired.com/ http://www.theatlantic.com/world/ ).

- Layout Managers. Κυριότεροι: Frame Layout, Linear Layout, Relative Layout

- Frame: ιδανικό για απλές περιπτώσεις όπου στην οθόνη έχουμε μόνο ένα συστατικό, όπως πχ μια λίστα

- Linear: ιδανικό για στίβαγμα συστατικων το ένα δίπλα στο άλλο ή το ένα κάτω απο το άλλο. Μας βοηθά επίσης να χωρίσουμε την οθόνη σε μέρη.

- Relative: δυνατό αλλα πολύπλοκο. Εδώ ορίζουμε τη διάταξη του κάθε συστατικού *σε σχέση* με κάποιο άλλο συστατικό


**Λίστες σε κινητές συσκευές**

- Χρήση ScrollView. Τι μπορεί να πάει στραβά; Πόσα στοιχεία χωράει η οθόνη; πόσα μπορώ να φορτώσω στη μνήμη; Παράδειγμα με 50 στοιχεία αν η οθόνη χωράει 10 πόσα πρέπει να φορτώσω;

- Τη λύση δίνει το ListView το οποίο φορτώνει δυναμικά τα στοιχεία και τα δημιουργεί λίγο πριν εμφανιστούν στην οθόνη. 

- Τί γίνεται με τα στοιχεία που είδαμε και έχουν πάει "επάνω". Συνεχίζουν να δεσμεύουν μνήμη. Επεξήγηση recycler

- Εισαγωγή στο MVC και το Adapter Pattern. 

- AdapterView: Προσαρμογέας, παρέχει τα δεδομένα προς το View, χωρίς να τον ενδιαφέρει τι είδους view είναι. Έτσι τα καιρικά δεδομένα μπορούν να παρουσιαστούν είτε σε ```ListView```, είτε σε ```GridView```

- Υλοποίηση του ListView: τροποποιούμε το ```fragment_mail.xml``` έτσι ώστε: 
  1. Να εμφανίζει ένα ```ListView``` αντί για ```TextView```
  2. Να έχει ```FrameLayout``` αντί για ```RelativeLayout```

- Το ListView πρέπει να γίνει:
```
<ListView
android:id="@+id/listview_forecast"
android:layout_width="match_parent"
android:layout_height="match_parent" />

```
- Ήρθε η ώρα να γεμίσουμε το ListView με δεδομένα. Ανοίγουμε το ```MainActivity.java```.

- Στην εσωτερική κλάση ```PlaceholderFragment``` στη μέθοδο ```onCreateView(...)``` εισάγουμε ένα array με dummy δεδομένα. Χρησιμοποιήστε αυτό αν θέλετε:

```
String[] data = {
                    "Mon 6/23 - Sunny - 31/17",
                    "Tue 6/24 - Foggy - 21/8",
                    "Wed 6/25 - Cloudy - 22/17",
                    "Thurs 6/26 - Rainy - 18/11",
                    "Fri 6/27 - Foggy - 21/10",
                    "Sat 6/28 - Error! - 23/18",
                    "Sun 6/29 - Sunny - 20/7"         };
```

- Επεξήγηση ροής δεδομένων στο ListView. (Σχετικό βίντεο: https://www.youtube.com/watch?v=uOOupBYZeO0)

![ListView](https://github.com/UomMobileDevelopment/Lesson02-material/blob/master/listViewDataHandlingModel.PNG)

- Γράφουμε κώδικα στη μέθοδο ```onCreateView(...)``` για να φτιάξουμε τον ```Adapter```. Στην περίπτωσή μας χρειαζόμαστε έναν ```ArrayAdapter```. Ο κατασκευαστής του παίρνει 4 παραμέτρους.
  1. Το context. Περιλαμβάνει όλες τις πληροφορίες για το περιβάλλον εκτέλεσης και δίνει πρόσβαση σε υπηρεσίες και αρχεία του συστήματος  (```getActivity()```)
  2. ID του list item layout. Θα το πάρουμε μέσω του καθολικού και ειδικού αρχείου R.java. Αυτό το αρχείο παρέχει ανθρώπινες ονομασίες (αντί για διευθύνσεις μνήμης) για όλα τα resources μας. Υπάρχει πάντα σε κάθε android project (```R.layout.list_item_forecast```)
  3. ID του text view (```R.id.list_item_forecast_textview```)
  4. Τη λίστα με τα δεδομένα (όπως ονομάσαμε το ArrayList)
  
Ας δώσουμε λίγη προσοχή στις ονομασίες απο το αρχείο R.java. Η μία ξεκινά με ```R.layout``` ενώ η άλλη με ```R.id```
αυτό υποδυκνύει πως η πρώτη μεταβλητή αναφέρεται σε αρχείο διάταξης xml ενώ η δεύτερη αναφέρεται σε συγκεκριμένο συστατικό xml.

- Κώδικας για να συνδέσουμε με τον ```Adapter``` με το ```ListView```. Αρχικά να 'πάρουμε' στα χέρια μας μία αναφορά προς το ListView χρησιμοποιώντας το ID που της έχουμε δώσει (```@+id/listview_forecast```). Υπενθύμιση η πρόσβαση στα ID μέσα απο τον κώδικα γίνεται με τη χρήση του ```R.java```. 
Λίγα λόγια για το πώς βρίσκουμε τα Views Με τη μέθodo ```findViewById()```

![Finding Views](https://github.com/UomMobileDevelopment/Lesson02-material/blob/master/findingViews.PNG)

Έτσι, ο κώδικας που πρέπει να γράψουμε είναι:
```
            ListView forecastListView = (ListView)rootView.findViewById(R.id.listview_forecast);
            forecastListView.setAdapter(forecastListAdapter);
```

και έτσι έχουμε συνολικά:

```
public static class PlaceholderFragment extends Fragment {

        public PlaceholderFragment() {
        }

        @Override
        public View onCreateView(LayoutInflater inflater, ViewGroup container,
                                 Bundle savedInstanceState) {
            View rootView = inflater.inflate(R.layout.fragment_main, container, false);
            // Create some dummy data for the ListView.  Here's a sample weekly forecast
            String[] data = {
                    "Mon 6/23 - Sunny - 31/17",
                    ///........
                    "Sun 6/29 - Sunny - 20/7"
            };
            List<String> weekForecast = new ArrayList<String>(Arrays.asList(data));

            ArrayAdapter<String> forecastListAdapter =
                    new ArrayAdapter<String>(
                            getActivity(),
                            R.layout.list_item_forecast,
                            R.id.list_item_forecast_textview, weekForecast);

            ListView forecastListView = (ListView)rootView.findViewById(R.id.listview_forecast);
            forecastListView.setAdapter(forecastListAdapter);


            return rootView;
        }
    }
```
