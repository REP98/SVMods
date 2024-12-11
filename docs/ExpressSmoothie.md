# Express Smoothie

Maquina para hacer batidos y merengadas

"Este es mi primer Mod espero que les guste" Nueva actualización compatible con Stardew Valley 1.6, ahora en ContentPatcher con
ExtraMachineConfig y CustomBush.

- Agrega una maquina de expreso y batidora que funciona con cualquier fruta del juego o de otros mods. También agrega un arbusto de limón criollo o latino y un árbol frutal de moriche así como el fabuloso papelón con limón.

## Agrega
- Batidos de frutas
- Merengadas de frutas
- Batido 3 en 1
- Paperón de limón

## Obtención

La receta de la maquina de Expresso te la da Alex con 5 Corazones de amistad

## Instalación y dependencia:

Esta Mods depende de:
- Smapi
- ContentPatcher
- MailFrameworkMod
- ExtraMachineConfig
- CustomBush
  
Una vez instaladas las dependecias solo descomprime y copia la carpeta Express Smoothie a la carpeta de mods.

## Desinstala:
Solo borra la carpeta Express Smoothie
Recomendación en partidas guardadas vender o descargar todos los productos obtenidos antes de desinstalar el mod.

Espero les guste.

---------------------------------------------------------------------------------------------------

## Nota:

Ahora gracias a las actualizaciones de ContentPatcher y Stardew Valley puedes crear tu mods he invocar mi maquina para añadir nuevos batidos aqui os dejo un ejemplo.

```json
{
    "Format": "2.4.0",
    "Changes": [
        // Carga tus Imagenes de tus objetos
        {
            "Action": "Load",
            "Target": "{{ModId}}/MyObject", 
            "FromFile": "assets/{{TargetWithoutPath}}.png"
        },
        // AÑADE TU LOGICA DE OBJECTOS
        // -----
        // AÑADE LA FUNCIONABILIDAD EN TU MODS A LA MAQUINA
        {
            "Action": "EditData",
			"Target": "Data/Machines",
			"TargetField": [
				"(BC)Soid64_MixerExpress",
				"OutputRules"
			],
            "Entries": {
                "{{ModId}}_StrawberryWithPineapple": {
                    "Id": "StrawberryWithPineapple",
                    "Triggers": [{ "RequiredItemId": "(O)400" }], // Fresa
                    "OutputItem": [{
                        "Id": "(O)Soid64_O_Milkshake",
                        "ItemId": "(O)Soid64_O_Milkshake",
                        "ObjectInternalName": "{0} Soid64_Milkshake",
                        "ObjectDisplayName": "[LocalizedText Strings\\Objects:Soid64_Milkshake %PRESERVED_DISPLAY_NAME]",
                        "CopyQuality": true,
                        "CopyColor":true,
                        "CopyPrice": true,
                        "PreserveId": "DROP_IN",
                        "PriceModifierMode": "Stack",
                        "PriceModifiers": [
                            {
                                "Modification": "Multiply",
                                "Amount": 3.0
                            },
                            {
                                "Modification": "Add",
                                "Amount": 50
                            }
                        ],
                        "CustomData": {
                            "selph.ExtraMachineConfig.CopyColor": "true",
                            "selph.ExtraMachineConfig.RequirementId.1": "(O)832", // Piña
                            "selph.ExtraMachineConfig.RequirementId.2": "(O)186", // Leche XL 
                            "selph.ExtraMachineConfig.RequirementInvalidMsg": "Require Milk and Pineapple"
                        }
                    }],
                    "MinutesUntilReady": 350
                },
                "{{ModId}}_fruits": {
                    "Id": "MyFruitss",
                    "Triggers": [{ "RequiredItemId": "(O){{ModId}}_fruits" }], // Fresa
                    "OutputItem": [{
                        "Id": "Default",
                        "ItemId": "(O){{ModId}}_fruits_out"
                    }],
                    "MinutesUntilReady": 250
                }
            },
            "MoveEntries": [
				{
					"ID": "{{ModId}}_StrawberryWithPineapple",
					"ToPosition": "Top"
				},
				{
					"ID": "{{ModId}}_fruits",
					"ToPosition": "Top"
				}
			]
        }
    ],
    "$schema": "https://smapi.io/schemas/content-patcher.json"
}
```
