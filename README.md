# Laravel Mobile Detect

Un package qui vous permet d'utiliser la détection des appareils directement dans vos modèles Blade. (Utilise la célèbre [bibliothèque de détection mobile PHP] (http://mobiledetect.net/), constamment mise à jour.)

### Quand utiliseriez-vous ce package ?
Le CSS réactif peut aider à rendre le contenu du navigateur agréable à regarder sur différents appareils, mais il ne vous aidera pas à servir un contenu réactif à partir de votre backend (du moins pas de la manière la plus simple). Cela peut avoir un très mauvais effet sur l'expérience de l'utilisateur (avez-vous déjà attendu le chargement d'une grande image alors que vous aviez une mauvaise connexion sur votre mobile ?) Ce package vous permettra de servir un contenu spécifique à un appareil directement depuis votre back-end.

### Comment fonctionne ce package ?
Le paquet met en œuvre diverses directives Blade que vous pouvez utiliser pour servir un contenu différent à partir de votre modèle Blade pour différents types d'appareils.

### Installation
Installer le paquet via composer :

```sh
$ composer require likewares/laravel-mobile-detect
```

### Laravel 5.4 ou antérieur
Ajoutez le service provider à votre fichier **config/app.php** :

```php
Riverskies\Laravel\MobileDetect\MobileDetectServiceProvider::class
```

Vous pouvez également ajouter un alias si vous souhaitez utiliser l'instance sous-jacente ailleurs (ou avoir accès à toutes les fonctions) :
```php
'MobileDetect' => Riverskies\Laravel\MobileDetect\Facades\MobileDetect::class
```

### Utilisation
Utilisez les nouvelles directives Blade dans vos fichiers modèles :

```php
@desktop
    <img src="/path/to/high-definition/image"/>
@elsedesktop
    <img src="/path/to/handheld-optimised/image"/>
@enddesktop
```

> **NOTE** Vous devrez peut-être exécuter `php artisan view:clear` pour que les nouvelles directives Blade prennent effet !

### Directives disponibles
`@desktop`, `@elsedesktop`, `@enddesktop` - pour les appareils destkop

`@handheld`, `@elsehandheld`, `@endhandheld` - pour les appareils autres que les ordinateurs de bureau (mobiles et tablettes)

`@tablet`, `@elsetablet`, `@endtablet` - pour les appareils tablettes

`@nottablet`, `@elsenottablet`, `@endnottablet` - pour les appareils autres que les tablettes (de bureau ou mobiles)

`@mobile`, `@elsemobile`, `@endmobile` - pour les appareils mobiles

`@notmobile`, `@elsenotmobile`, `@endnotmobile` - pour les appareils non mobiles (ordinateur de bureau ou tablette)

`@ios`, `@elseios`, `@endios` - for iOS platforms

`@android`, `@elseandroid`, `@endandroid` - pour les plateformes Android

The usage of `@else...` sont optionnelles.
