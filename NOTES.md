# NOTES — Ioo Paula-Antonia

## 1. Bug-urile găsite

Pentru fiecare bug, scrie 2-3 propoziții:

### Bug #1
- **Unde era:** `POST /events`, în fișierul `app/main.py`.
- **Cum l-am găsit:** Am rulat `python -m pytest -v` și a picat testul `test_create_event_returns_201`; endpoint-ul returna `200 OK` în loc de `201 Created`, cum ar fi normal pentru creare.
- **Cum l-am fixat:**

### Bug #2
- **Unde era:** Funcția `list_events` din fișierul `app/storage.py`.
- **Cum l-am găsit:** Am rulat `python -m pytest -v` și au picat testele `test_list_events_includes_created_items` și `test_list_events_paginates_without_overlap`; endpoint-ul returna mai puține evenimente decât ar fi trebuit și ceva nu era în regulă nici la paginare.
- **Cum l-am fixat:**

### Bug #3
- **Unde era:** Funcțiile `list_events` și `soft_delete_event` din fișierul `app/storage.py`.
- **Cum l-am găsit:** Am rulat `python -m pytest -v` și au picat testele `test_list_events_hides_soft_deleted_items`, `test_delete_same_event_twice_changes_response` și `test_pagination_after_delete_stays_consistent`; același event șters de două ori întorcea `204`, deși nu ar fi trebuit, iar eventurile șterse încă apăreau în listă.
- **Cum l-am fixat:**

---

## 2. Endpoint-ul nou

- **Decizii de design:** (ce-ai considerat? ce ai ales și de ce?)
- **Cazuri edge pe care le-ai acoperit:**
- **Teste adăugate:** (ce verifică fiecare)

---

## 3. Folosirea AI-ului

Fii cinstit. Nu pierzi puncte dacă spui adevărul, dimpotrivă.

- **Ce ai folosit:** (ChatGPT / Cursor / Copilot / altele)
- **Prompturi reprezentative folosite:** (scrie prompturile pe care le consideri relevante + context scurt: la ce te-au ajutat)
- **Unde te-a ajutat cel mai mult:**
- **Unde te-a încurcat sau ți-a dat un răspuns greșit:** (foarte interesant pentru noi!)
- **Cum ai verificat ce-a generat:**
- **Anexă opțională — export chat:** (dacă vrei, poți adăuga un export de chat relevant)

---

## 4. Ce-ai face cu mai mult timp

(Lista scurtă, 3-5 puncte. Arată-ne că ai văzut limitele actuale.)

---

## 5. Întrebări / observații

(Orice nu a fost clar, orice ai vrea să discuți cu noi.)
