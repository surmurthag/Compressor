# Compressor

## Installation debian11

Pour pouvoir utiliser ce script, vous devez installer les outils nécessaires. Exécutez les commandes suivantes dans votre terminal :
sudo npm install -g uglifycss
sudo npm install -g html-minifier
npm install -g uglify-js




<h1>Compressor</h1>

<p>Ouvrez votre éditeur de texte et créez un nouveau fichier nommé <code>Compressor</code>.</p>

<p>Ajoutez les commandes souhaitées dans le fichier <code>Compressor</code>. Voici le contenu du fichier en fonction des commandes que vous avez fournies :</p>

<pre><code>#!/bin/bash

# 1. Git Pull
git pull

# 2. Compression HTML
find templates -type f -name "*.html.twig" -exec sh -c 'sudo html-minifier "$0" --output "$0" --overwrite' {} \;

# 3. Compression CSS dans le dossier public/assets/
cd public/assets/
for file in *.css; do sudo uglifycss "$file" > "$file.tmp" &amp;&amp; mv "$file.tmp" "$file"; done
cd ../..

# 4. Compression JS dans le dossier public/build/js/
cd public/build/js
for file in *.js; do sudo uglifycss "$file" > "$file.tmp" &amp;&amp; mv "$file.tmp" "$file"; done
cd ../../..

# 5. Clear Cache
php bin/console cache:clear --env=prod
</code></pre>

<p>Enregistrez le fichier <code>Compressor</code>.</p>

<p>Maintenant, pour exécuter le fichier <code>Compressor</code>, vous devez vous assurer qu'il est exécutable. Vous pouvez le faire en utilisant la commande suivante dans le terminal :</p>

<pre><code>chmod +x Compressor</code></pre>

<p>Ensuite, vous pouvez exécuter le fichier en utilisant la commande suivante :</p>

<pre><code>./Compressor</code></pre>

<p>Assurez-vous d'exécuter cette commande depuis le répertoire racine de votre projet Symfony 6.2.</p>

