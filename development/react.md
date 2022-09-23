# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- l'état (_state_) pour contrôler l'affichage d'un composant ✔️
- les composants enfants et les _props_ qu'on leur passe ✔️
- le déclenchement d'instructions en fonction des actions de l'utilisateur ✔️
- le déclenchement d'instructions en fonction de l'étape du cycle de vie du composant ou du changement de valeur de ses props ✔️
- l'usage d'un reducer (_useReducer_) pour gérer un état composé dans un composant ✔️
- l'état stocké dans un composant avec un _context provider_ et accessible dans ses descendants via `useContext` ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```jsx
// reducer qui ajoute ou retire un destinataire du state
const reducer = (state, action) => {
  switch (action.type) {
    case "toggle_recipient":
      var found = false;
      for (let n = 0; n<state.length; n++) {
        if (state[n].id === action.payload.id) {
          found = true;
          break;
        }
      }
      if (!found) {
        return [...state, action.payload];
      } else {
        return state.filter(personne => personne.id !== action.payload.id);
      }

  }
};

function App() {
    const [titleInput, setTitleInput] = useState("");
    const [bodyInput, setBodyInput] = useState("");
    const [lists, setLists] = useState([]);
    const [recipients, setRecipients] = useState([]);

    useEffect(() => {
        const dataArray = [];
        /** handleWidgets */
        // Fetch des données au chargement depuis firebase
        studentsGroupsDB
            .once("value", (snap) => {
                Object.keys(snap.val()).map((classe) => {
                    const objet = {};
                    objet[classe] = snap.val()[classe];
                    dataArray.push(objet);
                });
            })
            .then(function () {
                setLists(dataArray);
            });
    }, []);

    // Initialisation du reducer
    const [destinataires, dispatch] = useReducer(reducer, [])

    const feu = () => {
        let recipientsString = "";
        // concaténation des emails
        for (let n = 0; n < destinataires.length; n++) {
            recipientsString += destinataires[n].email + ",";
        }
        window.open(`https://webmel.u-bordeaux.fr/h/search?action=compose&to=${recipientsString.substring(0, recipientsString.length - 1)}&subject=${titleInput}&body=${bodyInput}`);
    }

    return (
        <div className="App">
            <GlobalStyle/>

            <StyledDestinataires>{destinataires.map((receiver) => (
                <Etiquette id={receiver.id} mail={receiver.email} dispatch={dispatch}/>
            ))}</StyledDestinataires>
            <MailTitleInput
                titleInput={titleInput}
                setTitleInput={setTitleInput}
            ></MailTitleInput>
            <MailBodyInput
                bodyInput={bodyInput}
                setBodyInput={setBodyInput}
            ></MailBodyInput>
            <SendButton feu={feu}/>
            <ButtonList // On passe le dispatch aux boutons
                dispatch={dispatch}
                lists={lists}
                toggleRecipient={toggleRecipient}
            ></ButtonList>
        </div>
    )
}

```

### Utilisation dans un projet ✔️

[lien github](https://github.com/Hugo-M33/better-reacts-web)

Description :

### Utilisation en production si applicable ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ✔️

Description : Refonte du site web de [Consoneo](https://consoneo.com/) avec Next.JS, strapi, graphql

## 🌐 J'utilise des ressources

### Documentation React

- https://reactjs.org/docs/getting-started.html
- Documentation officielle de React

## 🚧 Je franchis les obstacles

### Point de blocage ❌

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
