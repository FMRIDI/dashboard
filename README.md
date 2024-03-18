# dashboard
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard des jours de récupération</title>
    <style>
        /* Styles CSS */
    </style>
    <!-- Inclure jQuery -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
</head>
<body>

<div class="header">
    <h1>JOURS DE RECUPERATION 24/7</h1>
</div>

<!-- Formulaire de connexion -->
<div id="loginForm" style="display: none;">
    <h2>Connexion</h2>
    <input type="text" id="username" placeholder="Nom d'utilisateur"><br>
    <input type="password" id="password" placeholder="Mot de passe"><br>
    <button onclick="login()">Se connecter</button>
</div>

<table id="recuperationTable">
    <!-- Tableau HTML -->
</table>

<script>
    // Nom d'utilisateur et mot de passe autorisés
    const validUsername = "votre_nom_utilisateur";
    const validPassword = "votre_mot_de_passe";

    // Fonction pour afficher le formulaire de connexion
    function showLoginForm() {
        document.getElementById('loginForm').style.display = 'block';
    }

    // Fonction pour masquer le formulaire de connexion
    function hideLoginForm() {
        document.getElementById('loginForm').style.display = 'none';
    }

    // Fonction pour vérifier les informations d'identification
    function login() {
        const username = document.getElementById('username').value;
        const password = document.getElementById('password').value;

        if (username === validUsername && password === validPassword) {
            // Masquer le formulaire de connexion et activer la modification du tableau
            hideLoginForm();
            enableTableEditing();
        } else {
            // Afficher un message d'erreur
            alert('Nom d\'utilisateur ou mot de passe incorrect.');
        }
    }

    // Fonction pour activer la modification du tableau
    function enableTableEditing() {
        // Récupérer le tableau
        const table = document.getElementById('recuperationTable');

        // Ajouter un écouteur d'événement pour capturer les modifications
        table.addEventListener('change', function(event) {
            // Vérifier si l'élément modifié est un champ de saisie de nombre
            if (event.target.tagName === 'INPUT' && event.target.type === 'number') {
                // Mettre à jour le contenu de la cellule avec la nouvelle valeur
                event.target.parentNode.nextElementSibling.textContent = event.target.value;
                
                // Envoyer les données modifiées au serveur avec AJAX (si nécessaire)
            }
        });
    }

    // Afficher le formulaire de connexion au chargement de la page
    window.onload = function() {
        showLoginForm();
    };
</script>

</body>
</html>
