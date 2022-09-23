# Langage Javascript

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les `structures` de base du langage ✔️
- les normes `ecmascript` ✔️
- l'utilisation de l'`asynchrone` ✔️
- les spécifités du mot-clef `this` ❌ / ✔️

## 💻 Je code en Javascript

### Un exemple de code commenté ✔️

```js
// customers est une liste de temps de traitement pour chaque client en secondes
// n est le nombre de caisses ouvertes
// Doit retourner le temps d'attente total, sachant qu'un client commence son checkout dès que la caisse est libre
function queueTime(customers, n) {
    //  tills est un tableau de n caisses, chacune avec un temps de traitement à 0
    const tills = Array.from(Array(n), () => 0)

    // Pour chaque client, on cherche la caisse libérée en première (celle qui a le temps le plus bas)
    for (let time of customers) {
        // ce reducer retourne un tableau [tempsTotalDuneCaisseLePlusBas,IndexDeLaCaisse]
        // Si le temps de traitement est le même, on prend la caisse la plus à gauche
        // Si une caisse a moins de temps qu'une autre avant, elle est remplacée dans l'accumulateur avec son indice
        let [lowestVal, lowestIndex] = tills.reduce((acc,v,i) => v < acc[0] ? [v,i] : acc, [tills[0], 0])
        tills[lowestIndex] += time
    }
    // On retourne le temps de la caisse la plus utilisée
    return Math.max(...tills)
}
```

### Utilisation dans un projet ✔️

[lien github](https://github.com/Hugo-M33/better-reacts-bot)

Description : Petit Bot discord pour permettre l'envoi de médias depuis une BDD, avec les [serverless functions de netlify](https://github.com/Hugo-M33/better-reacts-web/tree/main/functions), [discord.js](https://discord.js.org/#/) et le [SDK firebase](https://firebase.google.com/)

### J'ai utilisé ce langage en production ❌ / ✔️

[lien du projet](...)

Description :

### J'ai utilisé ce langage en environement professionnel ❌ / ✔️

Description :

## 🌐 J'utilise des ressources

### MDN

- https://developer.mozilla.org/fr/
- Documentation communautaire maintenue par Mozilla à destination des dev Web

## 🚧 Je franchis les obstacles

### Point de blocage ❌

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌
- J'ai fait une [présentation](...) ❌

