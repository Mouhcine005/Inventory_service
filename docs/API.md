# API Inventory

Toutes les réponses d'erreur : `{ "message": "...", "requestId": "..." }`.
200 = succès ; 400 = entrée invalide ; 401 = session absente/invalide ; 403 = propriétaire/acteur interdit ; 404 = ressource absente ; 409 = conflit métier ; 503 = service dépendant indisponible.

| Service | Methode / chemin | Entree | Sortie |
|---|---|---|---|
| Inventory | GET /api/inventory/{productId} | public | productId,stock |
| Inventory | POST /api/inventory/check | items:[{productId,quantity}] | available |
| Inventory | POST /api/inventory/reserve | items, reservationId optionnel ; appel interne | success,reservationId |
| Inventory | POST /api/inventory/release | items,reservationId ; appel interne | success |

GET /health est public et renvoie le nom du service et son etat.

Reserve et release exigent X-Internal-Key. Une reservationId permet la deduplication et empeche une double restitution du stock.
