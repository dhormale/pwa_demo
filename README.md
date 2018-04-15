#Changes for PWA application:


.angular-cli.json	=>	"serviceWorker": true,

package.json		=>	"@angular/service-worker": "^5.2.9",

index.html		    =>	<link rel="manifest" href="assets/manifest.json">
        				<meta name="theme-color" content="#317EFB"/>
		        		<meta name="Description" content="PWA TEST">
				        <noscript>Enable JavaScript to view this web page.</noscript>

main.ts			=>	platformBrowserDynamic().bootstrapModule(AppModule)  
					.then(() => {
						if ('serviceWorker' in navigator) {
							navigator.serviceWorker.register('ngsw-worker.js');
						}
                    })
					.catch(err => console.log(err));

ngsw-config.json	=>

{
    "index": "/index.html",
    "assetGroups": [
        {
            "name": "app",
            "installMode": "prefetch",
            "resources": {
                "files": [
                    "/favicon.ico",
                    "/index.html"
                ],
                "versionedFiles": [
                    "/*.bundle.css",
                    "/*.bundle.js",
                    "/*.chunk.js"
                ]
            }
        },
        {
            "name": "assets",
            "installMode": "lazy",
            "updateMode": "prefetch",
            "resources": {
                "files": [
                    "/assets/**"
                ]
            }
        }
    ]
}


assets > manifest.json		=>

{
    "dir": "ltr",
    "lang": "en",
    "name": "PWA TEST",
    "scope": "/",
    "display": "standalone",
    "start_url": "/index.html",
    "short_name": "NF",
    "icons": [
        {
        "src": "/assets/logo.png",
        "sizes": "256x256",
        "type": "image/png"
        },
        {
        "src": "/assets/logo.png",
        "sizes": "512x512",
        "type": "image/png"
        }
    ],
    "theme_color": "#f27b00",
    "description": "",
    "orientation": "any",
    "background_color": "#3a1c8d",
    "related_applications": [],
    "prefer_related_applications": false
}
