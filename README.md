# 🐾 React Animali - Progetto con Componenti, Modale e API

Questo progetto React guida lo sviluppo passo-passo di un componente dinamico per gestire una lista di animali, con l'aggiunta di una modale interattiva e l'integrazione con una API.

---

## 📌 Milestone 1: Inserire un Componente React

**Obiettivo:** Mostrare una lista base di animali dentro un `<details>` espandibile.

### Requisiti:
- Monta un componente React dentro un elemento con classe `.lista-animali`.
- Il componente deve contenere:
  - Un elemento `<details>` con titolo **"Animali"**.
  - Una lista `<ul>` generata a partire da un array statico di stringhe `animals`.

---

## 📌 Milestone 2: Aggiungere Animali Casuali

**Obiettivo:** L’utente può aggiungere animali dinamicamente alla lista cliccando un bottone.

### Requisiti:
- Usa `useState` per gestire l’array `animals` (inizialmente vuoto).
- Aggiungi un bottone **"Aggiungi Animale"** sopra il `<details>`.
- Alla pressione del bottone, aggiungi un animale casuale alla lista.
- Usa questo array per la scelta casuale:
  ```js
  const animalsChoices = ["Cane", "Gatto", "Pappagallo", "Cavallo", "Panda"];
  ```

---

## 📌 Milestone 3: Usare una Modale per Aggiungere Animali

**Obiettivo:** L’utente può inserire manualmente il nome dell’animale da aggiungere, tramite una modale.

### Requisiti:
- Parti dal seguente componente `Modal`:
  ```jsx
  function Modal({
        title, 
        content, 
        show = false, 
        onClose = () => {}
    }){
        return show && ReactDOM.createPortal(
            <div className="modal-container">
                <div className="modal">
                    <h2>{title}</h2>
                    <p>{content}</p>
                    <button onClick={onClose}>Annulla</button>
                </div>
            </div>,
            document.body
        );
    }
  ```

- Espandi la modale per:
  - Usare `content` per passare **un componente JSX** (es. un input).
  - Aggiungere in fondo alla modale due bottoni:
    - **Annulla** (`onClose`)
    - **Conferma** (`onConfirm`)
- Quando l’utente clicca **"Aggiungi Animale"**, apri la modale.
- Dentro la modale, l’utente inserisce il nome dell’animale tramite input.
- Al click su **Conferma**:
  - L’animale viene aggiunto alla lista.
  - La modale si chiude.

---

## 🎯 Bonus: Utilizzare l'API per Creare Card

**Obiettivo:** Aggiungere animali specifici usando un'API e mostrarli in formato card.

### Requisiti:
- Usa l'API locale:
  ```
  http://localhost:3333/animals?search=[animalName]
  ```
- Al click su **Conferma** della modale:
  - Effettua la richiesta con il nome inserito.
  - Mostra uno stato di caricamento (es. “Caricamento...”).
- Se l'API restituisce risultati:
  - Crea un oggetto con:
    - `name`: Nome dell’animale
    - `description`: Descrizione (o "Descrizione non disponibile")
    - `image`: URL dell’immagine (o immagine di default)
  - Mostra l'animale come una **card** contenente:
    - Titolo (nome)
    - Immagine
    - Descrizione
- Se non ci sono risultati:
  - Mostra un messaggio di errore: `"Nessun animale trovato"`
- In caso di errore di rete:
  - Mostra un messaggio di errore: `"Errore durante la ricerca dell'animale"`

---

## 🛠 Stili Modale

```css
.modal-container {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.75);
    display: flex;
    justify-content: center;
    align-items: center;
}

.modal {
    background-color: white;
    padding: 20px;
    border-radius: 5px;
}
```

---

## ✅ Funzionalità Finali

- [x] Lista visibile con `<details>`
- [x] Aggiunta dinamica con animale casuale
- [x] Modale con input e bottoni
- [x] Integrazione API per mostrare card con info e immagine
- [x] Gestione messaggi di errore e caricamento

---

Buon lavoro! 💻🐶