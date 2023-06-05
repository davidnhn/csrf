# CSRF 

CSRF (Cross-Site Request Forgery), également connu sous le nom d'attaque "session riding" ou "one-click attack", est une vulnérabilité de sécurité qui peut affecter les applications web. Elle se produit lorsque des actions non autorisées sont exécutées au nom d'un utilisateur authentifié sans son consentement.

Voici comment fonctionne une attaque CSRF :

L'utilisateur authentifié se connecte à une application web et reçoit un jeton de session pour maintenir sa connexion.

Pendant que l'utilisateur est encore authentifié, il visite un autre site malveillant ou clique sur un lien malveillant sur un site tiers.

Ce site malveillant contient une requête vers l'application web ciblée, mais cette requête est masquée et exécutée automatiquement sans que l'utilisateur en ait conscience.

La requête malveillante utilise les cookies ou les informations de session de l'utilisateur authentifié pour exécuter des actions non autorisées, telles que supprimer des données, effectuer des achats, ou apporter des modifications indésirables.

La protection CSRF consiste à s'assurer que chaque requête effectuée sur le serveur provient d'une source légitime et a été intentionnellement initiée par l'utilisateur lui-même. Pour éviter les attaques CSRF, les applications web utilisent généralement une mesure de protection appelée "jeton CSRF" ou "jeton anti-CSRF".

Le jeton CSRF est un jeton unique et aléatoire généré par l'application pour chaque session ou formulaire. Il est ensuite inclus dans les formulaires ou les requêtes AJAX pour vérifier l'authenticité de la source de la requête.

Voici comment fonctionne la protection CSRF avec un jeton CSRF :

Lorsqu'un utilisateur authentifié accède à une application web, un jeton CSRF unique est généré et associé à sa session.

Lorsque l'utilisateur soumet un formulaire ou effectue une requête POST, le jeton CSRF est inclus dans la requête, généralement dans un champ de formulaire caché ou dans l'en-tête de la requête.

Lorsque le serveur reçoit la requête, il vérifie si le jeton CSRF fourni correspond à celui qui a été généré pour la session en cours. Si les jetons correspondent, la requête est considérée comme légitime et est traitée normalement. Sinon, une erreur CSRF est générée.

La protection CSRF empêche les attaques CSRF en vérifiant que chaque requête est accompagnée d'un jeton CSRF valide, ce qui rend extrêmement difficile pour un attaquant de reproduire ce jeton et de l'inclure dans une requête malveillante.

Dans Laravel, la protection CSRF est activée par défaut. Lorsque vous incluez la directive @csrf dans vos formulaires Blade, un champ de formulaire caché contenant le jeton CSRF sera automatiquement généré. Lorsque vous soumettez le formulaire, Laravel vérifiera automatiquement la validité du jeton CSRF avant de traiter la requête. Cela contribue à prévenir les attaques CSRF dans votre application Laravel.
