# Framer Copy-Pasta

## Presse-papiers Framer
 
Une petite page web, en un seul fichier HTML, pour **lire, stocker et recoller** les éléments copiés depuis [Framer](https://www.framer.com).
 
## Le problème
 
Quand on copie un élément dans Framer (Cmd-C), on peut le recoller dans un autre projet Framer, mais pas ailleurs : dans un éditeur de texte, Cmd-V ne fait rien.
 
En réalité, le contenu est bien dans le presse-papiers. Framer y dépose du HTML qui ne contient qu'un `<span>` vide, et toutes les données y sont cachées dans un attribut, sous forme de JSON :
 
```html
<span data-framer-pasteboard="{ …calques, textes, styles… }"
      data-framer-pasteboard-type="application/x-framer-layers"></span>
```
 
Un éditeur de texte colle donc… rien de visible.
 
## Ce que fait cette page
 
**Lire un collage Framer**

- Extrait le **texte** de tous les calques texte, prêt à copier.
- Liste les **images**, avec un lien vers le fichier hébergé par Framer.
- Affiche les **icônes SVG** et permet de les télécharger en `.svg`.
- Montre l'**arborescence des calques** et le **JSON complet**.
 
**Stocker et recoller**

- Enregistre les collages dans une **bibliothèque**, gardée dans le navigateur.
- **Copier pour Framer** remet un collage dans le presse-papiers, exactement tel que Framer l'avait produit. Il suffit ensuite de faire Cmd-V dans Framer.
- Exporte et importe les collages en fichiers `.framerclip.json`, pour les sauvegarder ou les partager.
- 
## Utilisation
 
1. Téléchargez `framer-presse-papiers.html` et ouvrez-le dans un navigateur (Chrome conseillé).
2. Dans Framer, sélectionnez des éléments et faites **Cmd-C**.
3. Cliquez dans la page, puis faites **Cmd-V** : le contenu s'affiche.
4. Donnez un nom au collage, puis cliquez sur **Enregistrer dans la bibliothèque**.
5. Plus tard, cliquez sur **Copier pour Framer**, puis faites **Cmd-V** dans Framer.
Aucune installation et aucun serveur : tout se passe localement dans le navigateur. La page peut aussi être publiée avec GitHub Pages.
 
## Formats reconnus
 
| Origine de la copie | Type | Particularités |
|---|---|---|
| Copie directe dans Framer | `application/x-framer-layers` | Images sous forme de référence à un fichier hébergé par Framer |
| Plugin Figma « Figma to HTML with Framer » | `application/x-framer-figma-plugin` | Icônes SVG incluses en entier |
 
## Limites
 
- **Format non officiel.** Le format du presse-papiers de Framer n'est pas documenté et peut changer lors d'une mise à jour. Un ancien collage pourrait alors ne plus être accepté.
- **Images.** Le collage contient seulement une référence vers l'image hébergée par Framer, pas l'image elle-même. Elle peut ne pas revenir si elle a été supprimée ou si on colle dans un autre projet.
- **Styles et polices.** Un collage peut faire appel à des styles du projet d'origine (par exemple « Body »), qui pourraient manquer ailleurs.
- **Bibliothèque locale.** Elle est stockée dans le navigateur (`localStorage`) : vider les données du navigateur l'efface. Pensez à l'exporter régulièrement.
 
## Avertissement
 
Projet indépendant, sans lien avec Framer B.V. « Framer » est une marque de son propriétaire.
 
