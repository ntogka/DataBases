# DataBases
Ένα project με βάση στο AWS RDS δεσμεύοντας ένα μηχάνημα στο AWS με εγκατεστημένη postgreSQL. Δουλεύτηκε μέσω pgAdmin4

V.1

Σκοπός:

Φτιάχτηκε μια βάση δεδομένων για την αποθήκευση και εξερεύνηση δεδομένων που προέρχονται από την Airbnb. Η βάση δεδομένων αποτελείται από μία συλλογή πινάκων και τις μεταξύ τους
σχέσεις.Για να οριστεί το σχήμα της βασίστηκα στη μορφή των δεδομένων εισόδου, το οποίο απεικονίστικε σε ένα διάγραμμα ER.
Δημιουργήθηκαν πίνακες χρησιμοποιώντας SQL και θα εισάχθηκαν δεδομένα σε αυτούς με την εντολή \copy. Επίσης, δημιουργήθηκαν περιορισμοί ξένου κλειδιού για αναφορική ακεραιότητα.

Δεδομένα:
https://drive.google.com/open?id=1mrrXKz3RusWOUrhR0ap8nb2G2elIAjXz

Τι φτιάχτηκε:

● Ένα διάγραμμα ER με τους Airbnb πίνακες, τις σχέσεις και τις ιδιότητές τους.
● Τη βάση δεδομένων Airbnb σε ένα Postgres Cloud instance.
● Η βάση αυτή θα πρέπει να περιέχει πίνακες για τους οποίους θα ισχύουν τα εξής:
○ κάθε πίνακας να αντιστοιχεί σε ένα αρχείο .csv του Airbnb dataset.
○ να έχουν εισαχθεί σε αυτόν τα αντίστοιχα δεδομένα.
○ να περιέχει περιορισμούς πρωτεύοντος και/ή ξένου κλειδιού.

Tip:

Επειδή μερικές εντολές create table έχουν πολλά πεδία, όπως αυτή για τον πίνακα Listing, τρέχω το python πρόγραμμα gen_ddl_python3.py, το οποίο παίρνει ως παράμετρο το .csv αρχείο
των δεδομένων, π.χ. listings.csv για τον πίνακα Listing, και παράγει ένα αρχείο .sql με την εντολή create table για τον αντίστοιχο πίνακα. 


V.2

Σκοπός:

Εξερεύνηση δεδομένων του Airbnb με ερωτήματα σε SQL

Τι φτιάχθηκε:

● 12 SQL ερωτήματα που θα περιλαμβάνουν inner join, outer join, where,
order by, group by, limit, καθώς και χρησιμοποίηση των συναρτήσεων min,
max, avg, της λέξης κλειδί distinct, καθώς και χρησιμοποίηση των τελεστών
σύγκρισης like, between.
● Κάθε ερώτημα θα πρέπει να συνοδεύεται από μια μικρή περιγραφή που θα εξηγεί ποιος
είναι ο σκοπός του δηλαδή τι ζητάμε. Επίσης θα συνοδεύεται και από το πλήθος των
εγγραφών που επεστράφησαν ως αποτέλεσμα.
● Κάθε πίνακας εκ των Calendar, Listings, Reviews, Neighbourhoods, Geolocation θα
πρέπει να χρησιμοποιηθεί σε τουλάχιστον ένα ερώτημα.
● Τουλάχιστον 8 ερωτήματα θα πρέπει να περιέχουν ένα τουλάχιστον join.
● Τουλάχιστον 2 ερωτήματα θα πρέπει να περιέχουν ένα τουλάχιστον outer join


V.3

Σκοπός:

Αλλαγές στον σχεδιασμό της βάσης ώστε να κανονικοποιηθεί και να αποφευχθούν ανωμαλίες.

Ζητούμενα Εργασίας:

1. Πίνακας Host - αρχείο host_table.sql
● Δημιουργήστε έναν νέο πίνακα Host ο οποίος θα έχει τα εξής πεδία του Listings:
table Host: host_id, host_url, host_name, host_since, host_location, host_about,
host_response_time, host_response_rate, host_acceptance_rate, host_is_superhost,
host_thumbnail_url, host_picture_url, host_neighbourhood, host_listings_count,
host_total_listings_count, host_verifications, host_has_profile_pic, host_identity_verified,
calculated_host_listings_count. Δηλαδή τα πεδία αυτά να πάρουν τις τιμές του Listings.
● Φτιάξτε τα πεδία του Host να έχουν ονόματα χωρίς το ‘host_’ πρόθεμα.
● Διαγράψτε τα αντιγραφέντα host πεδία από τον Listings εκτός από το host_id.
● Δηλώστε κατάλληλο Primary Key στον Host.
● Δηλώστε κατάλληλο Foreign Key στον Listings με αναφορά στον Host.

2. Πίνακας Room - αρχείο room_table.sql
● Δημιουργήστε έναν νέο πίνακα Room ο οποίος θα έχει τα εξής πεδία του Listings:
table Room: listing_id, accommodates, bathrooms, bedrooms, beds, bed_type,
amenities, square_feet, price, weekly_price, monthly_price, security_deposit. Δηλαδή τα
πεδία αυτά να πάρουν τις τιμές του Listings.
● Διαγράψτε τα αντιγραφέντα room πεδία από τον Listings.
● Δηλώστε κατάλληλο Foreign Key στον Room με αναφορά στον Listings.
● Διαγράψτε τα αντιγραφέντα πεδία από τον Listings εκτός από το listing_id.

3. Πίνακας Price - αρχείο price_table.sql
● Δημιουργήστε έναν νέο πίνακα Price ο οποίος θα έχει τα εξής πεδία του Listings:
table Price: listing_id, price, weekly_price, monthly_price, security_deposit, cleaning_fee,
guests_included, extra_people, minimum_nights, maximum_nights,
minimum_minimum_nights, maximum_minimum_nights, minimum_maximum_nights,
maximum_maximum_nights, minimum_nights_avg_ntm, maximum_nights_avg_ntm.
Δηλαδή τα πεδία αυτά να πάρουν τις τιμές του Listings.
● Αλλάξτε τους τύπους πεδίων δεκαδικών αριθμών και χρημάτων σε νέο κατάλληλο
τύπο(μπορεί να χρειαστεί να αφαιρέσετε κάποιο σύμβολο hint:replace()).
● Διαγράψτε τα αντιγραφέντα price πεδία από τον Listings.
● Δηλώστε κατάλληλο Foreign Key στον Price με αναφορά στον Listings.
● Διαγράψτε τα αντιγραφέντα πεδία από τον Listings εκτός από το listing_id.

4. Πίνακας Neighborhood - αρχείο location_table.sql
● Δημιουργήστε έναν νέο πίνακα Location ο οποίος θα έχει τα εξής πεδία του Listings:
table Location: listing_id, street, neighbourhood, neighbourhood_cleansed, city, state,
zipcode, market, smart_location, country_code, country, latitude, longitude,
is_location_exact. Δηλαδή τα πεδία αυτά να πάρουν τις τιμές του Listings.
● Διαγράψτε τα αντιγραφέντα location πεδία από τον Listings.
● Δηλώστε κατάλληλο Foreign Key στον location με αναφορά στον Listings.
● Διαγράψτε τα αντιγραφέντα πεδία από τον Listings εκτός από το listing_id.
● Διαγράψτε τη συχέτιση του πίνακα listing με τον πίνακα neighborhood και συσχετίστε
κατάλληλα τον πίνακα location με τον πίνακα neighborhood.

5. Πίνακας Calendar - αρχείο calendar.sql
● Ομοίως με τα αντίστοιχα πεδία του Price, αφαιρέστε τα σύμβολα που χρειάζεται ώστε να
επιτρέπεται το ALTER σε τύπο πεδίων δεκαδικών αριθμών για τα πεδία price,
adjustable_price, καθώς και να μεταρέψετε το πεδίο available σε πεδίο τύπου boolean.
Για όλους τους Πίνακες
● Μετονομάστε όλους τους πίνακες από πληθυντικό σε ενικό αριθμό. Δηλαδή Listing,
Review, κλπ. Τις εντολές αυτές παραδώστε τες σε αρχείο all_tables.sql
● Αλλάξτε το ER διάγραμμα ώστε να είναι σύμφωνο με τις αλλαγές που κάνατε. Φυσικά
δεν θα απεικονίζονται όλες οι αλλαγές στο ER και επίσης υπενθυμίζουμε σε πίνακες με
πολύ μεγάλο πλήθος πεδίων απλώς σχεδιάστε μερικά ενδεικτικά και όχι όλα.


V.4

Σκοπός:

Μερικές ακόμα αλλαγές κανονικοποίησης και έπειτα τρέχουμε ερωτήματα ομαδοποίησης και συνάθροισης

Ζητούμενα Εργασίας:

Μέρος Α

● Παρατηρήστε ότι οι τιμές του πεδίου amenities στον Πίνακα room_table που
δημιουργήσαμε στην προηγούμενη εργασία δεν είναι ατομικές. Προκειμένου να γίνει
κανονικοποίηση, δημιουργήστε έναν νέο Πίνακα Amenity με πεδία amenity_id και
amenity_name. Αποθηκεύστε στο amenity_name όλες τις μοναδικές ατομικές τιμές του
πεδίου amenities αφού επεξεργαστούν κατάλληλα (Μπορείτε να χρησιμοποιήσετε τις
String functions της postgres regexp_split_to_table(), regexp_replace() ή/και όποιες
άλλες θεωρείτε ότι σας βολεύουν). Δηλώστε το amenity_id ως πεδίο αυτόματης
προσαύξησης και κάντε το Primary Key.
● Κάντε τις ενέργειες που είναι απαραίτητες ώστε να υπάρχει σύνδεση του Πίνακα
room_table με τον Amenity. Οι ενέργειες αυτές μπορεί να περιλαμβάνουν δημιουργία
νέων πεδίων, ορισμό Primary/Foreign Keys μέχρι και δημιουργία νέου Πίνακα.
● Διαγράψτε το πεδίο amenities από τον room_table.
● Ενημερώστε το ER διάγραμμα της βάσης με τις αλλαγές.
Γράψτε όλες τις εντολές διαμόρφωσης της βάσης του Μέρους Α σε ένα αρχείο part1.sql.

Μέρος Β

Φτιάξτε 5 ερωτήματα συνάθροισης που να έχουν κάποιο νόημα.
● Όλα πρέπει να έχουν τουλάχιστον ένα join
● 2 από τα ερωτήματα θα πρέπει να έχουν τουλάχιστον ένα outer join.
● Τουλάχιστον 2 από τα ερωτήματα θα πρέπει να έχουν ένα WHERE.
● Τουλάχιστον 2 από τα ερωτήματα θα πρέπει να έχουν ένα GROUP BY..
● Τουλάχιστον 2 από τα ερωτήματα θα πρέπει να έχουν ένα HAVING.
● Τουλάχιστον σε 1 από τα ερωτήματα πρέπει να χρησιμοποιηθεί ο πίνακας geolocation.
● Θα πρέπει να χρησιμοποιηθούν όλοι οι πίνακες που φτιάξατε στην προηγούμενη
άσκηση (table Host, table Room, table Price, table Location)
Γράψτε όλα τα ερωτήματα σε ένα αρχείο part2.sql.


V.5
