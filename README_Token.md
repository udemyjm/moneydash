** Crée un jeton - À faire une fois **

GitHub → Settings → Developer settings → Fine-grained tokens → Generate =>
Token name : dashboard-bourse (le nom est libre).
Description : facultative. Tu peux mettre « Sync config dashboard ».
Resource owner : laisse udemyjm, c’est ton compte.
Expiration : 30 jours par défaut, soit jusqu’au 20 décembre. Passe à 90 jours ou 1 an (« Custom ») pour ne pas le recréer trop souvent. À la date d’expiration, le bouton ☁ passera en « erreur » et il faudra générer un nouveau jeton.
Repository access : choisis « Only select repositories », puis sélectionne ton dépôt du dashboard. « Public repositories » ne convient pas, car c’est en lecture seule : la sauvegarde échouerait.
Permissions : une fois « Only select repositories » choisi, une section Repository permissions apparaît. Clique sur « Add permissions », coche Contents, puis mets Access : Read and write. « Metadata : Read-only » s’ajoute tout seul et c’est normal. Ne touche pas aux « Account permissions ».
Clique ensuite sur Generate token et copie-le tout de suite (github_pat_…) : GitHub ne l’affiche qu’une fois.

** Fonctionnement du bouton **

Enregistrement : chaque modification (action, favori, disposition, thème) part sur GitHub environ 4 secondes plus tard. Le bouton ☁ indique l’état : à envoyer, synchronisé ou erreur. Chaque envoi crée un commit dans l’historique du dépôt.
Lecture : à l’ouverture, la page recharge la config GitHub si elle a changé.
Sans jeton : l’appareil est en lecture seule. Sur un dépôt public, tu peux consulter ton dashboard partout sans rien saisir.
Sans ressaisir propriétaire et dépôt : remplis la constante GITHUB en haut du script une fois. Il ne reste alors que le jeton à coller sur chaque appareil où tu veux modifier.
Sécurité du jeton : il reste seulement dans le navigateur de l’appareil, jamais dans le code ni dans le fichier de config. Limite-le à ce dépôt et donne-lui une date d’expiration.
Dépôt privé : la lecture demande le jeton sur tous les appareils.
Conflit : si GitHub et l’appareil ont tous deux changé, l’envoi s’arrête et le bouton ☁ passe en « conflit ». Tu choisis alors « Charger depuis GitHub » ou « Envoyer vers GitHub » dans la fenêtre.
