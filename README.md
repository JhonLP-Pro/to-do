# Application Todo List avec Vue.js

Une application moderne et interactive de gestion de tâches construite avec Vue 3 et Vite.

## 🌟 Fonctionnalités

- ✅ Ajouter des tâches
- 🗑️ Supprimer des tâches
- ✔️ Marquer les tâches comme terminées
- 📊 Voir le nombre de tâches terminées
- 🎯 Animations fluides pour une meilleure expérience utilisateur

## 🚀 Technologies Utilisées

- **Vue 3** - Framework JavaScript progressif
- **Vite** - Outil de build ultra-rapide
- **Composition API** - Pour une meilleure organisation du code
- **@vueuse/core** - Collection d'utilitaires Vue composables
- **CSS moderne** - Animations et transitions fluides

## 📁 Structure du Projet

```
todo-temp/
├── src/
│   ├── components/
│   │   └── TodoList.vue    # Composant principal de la liste de tâches
│   ├── App.vue            # Composant racine
│   └── main.js           # Point d'entrée de l'application
├── index.html           # Page HTML principale
└── package.json        # Dépendances et scripts
```

## 💻 Comment utiliser l'application

1. **Ajouter une tâche**
   - Tapez votre tâche dans le champ de saisie
   - Appuyez sur Entrée ou cliquez sur "Ajouter"

2. **Marquer une tâche comme terminée**
   - Cliquez sur la case à cocher à gauche de la tâche
   - Une animation indique que la tâche est terminée

3. **Supprimer une tâche**
   - Cliquez sur le bouton "Supprimer" à droite de la tâche
   - Une animation de glissement accompagne la suppression

## 🎨 Animations

L'application inclut plusieurs animations pour une meilleure expérience utilisateur :

- **Ajout de tâche** : Glissement depuis la gauche
- **Suppression de tâche** : Glissement vers la droite avec effet de fondu
- **Tâche terminée** : Animation de la case à cocher et du texte
- **Réorganisation** : Transition fluide lors des changements de liste

## 🛠️ Installation et Démarrage

1. **Installation des dépendances**
   ```bash
   npm install
   ```

2. **Lancement du serveur de développement**
   ```bash
   npm run dev
   ```

3. **Construction pour la production**
   ```bash
   npm run build
   ```

## 🔧 Personnalisation

Le code est organisé de manière modulaire et facile à personnaliser :

- Les styles sont définis dans des balises `<style>` scoped
- Les animations peuvent être ajustées dans les classes CSS
- La logique métier est séparée dans des fonctions composables

## 📝 Notes de Développement

- Utilisation de la Composition API pour une meilleure réutilisation du code
- Gestion d'état locale avec `ref` et `computed`
- Transitions Vue.js pour les animations de liste
- CSS moderne avec flexbox pour la mise en page
