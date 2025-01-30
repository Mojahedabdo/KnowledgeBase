---
title: Problèmes connus d'AdGuard pour Windows
sidebar_position: 10
---

:::info

Cet article parle de AdGuard pour Windows, un bloqueur de contenus multifonctionnel qui protège votre appareil au niveau du système. Pour voir comment il fonctionne, [téléchargez l'application AdGuard](https://agrd.io/download-kb-adblock)

:::

## Problèmes de compatibilité entre AdGuard pour Windows et AdGuard VPN pour Windows

Une fois installés, AdGuard pour Windows et AdGuard VPN commencent à fonctionner ensemble sans aucun effort de votre part. Cependant, la modification de certains de leurs paramètres par défaut peut entraîner un fonctionnement incorrect des applications lorsqu'elles s'exécutent en même temps.

Il existe deux paramètres spécifiques dans AdGuard pour Windows : *Utiliser le mode de pilote de redirection* et *Filtrer localhost*. By default, the first is disabled, and the second is enabled. Changing any of these settings will inevitably disrupt AdGuard's filtering if both AdGuard Ad Blocker and AdGuard VPN are enabled on your device.

Changing these settings is only necessary to resolve issues related to the simultaneous operation of AdGuard Ad Blocker and network-level apps such as antiviruses, VPNs, and network filters. If you come across a situation where you need to change the default state of the above settings and still want AdGuard Ad Blocker and AdGuard VPN to work simultaneously and correctly — [create an issue on GitHub](https://github.com/AdguardTeam/AdguardForWindows/issues/new/choose) so we can help you personally.

We are currently working on overcoming the above-listed limitations of the simultaneous work of our apps.
