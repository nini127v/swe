# NOTES — Ioo Paula-Antonia

## 1. Bug-urile găsite

Pentru fiecare bug, scrie 2-3 propoziții:

### Bug #1
- **Unde era:** `POST /events` in fisierul `app/main.py`
- **Cum l-am găsit:** am rulat `py -m pytest -v`, si a picat testul `test_create_event_returns_201`; returneaza `200 OK` in loc de `201 Created`, cum ar fi normal
- **Cum l-am fixat:** am adaugat `status_code=201` pentru `POST /events`, pentru ca endpoint-ul creeaza un event nou si nu ar trebui sa ramana pe default-ul `200 OK`

### Bug #2
- **Unde era:** functia `list_events` in fisierul `app/storage.py`
- **Cum l-am găsit:** am rulat `py -m pytest -v` si au picat: `test_list_events_includes_created_items` si `test_list_events_paginates_without_overlap`; returneaza mai putine evenimente decat ar fi trebuit si ceva nu e in regula nici la paginare
- **Cum l-am fixat:** am schimbat din `offset + 1 : offset + 1 + limit` in `offset : offset + limit`; sarea peste primul event creat

### Bug #3
- **Unde era:** functiile `list_events`, `soft_delete_event` in fisierul `app/storage.py`
- **Cum l-am găsit:** am rulat `py -m pytest -v` si au picat: `test_list_events_hides_soft_deleted_items`, `test_delete_same_event_twice_changes_response` si `test_pagination_after_delete_stays_consistent`; acelasi event sters de doua ori => `204`, desi nu ar fi trebuit + chiar daca s-au sters, ele apareau in lista inca
- **Cum l-am fixat:** in functia `list_events`, am adaugat o conditie de tip `if` pentru a nu mai permite afisarea events care au fost sterse; in `soft_delete_event`, am adaugat iar o conditie `if` pentru a returna `None` daca event a fost deja sters, ca sa nu mai fie permis al doilea delete daca se incearca

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
