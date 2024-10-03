# Lab 9: Implementing Azure Load Balancer and Traffic Manager

## Objectif
L'objectif de ce laboratoire est de déployer un Azure Load Balancer pour distribuer le trafic entre plusieurs machines virtuelles (VM), configurer des sondes de santé et des règles de répartition de charge, mettre en place Azure Traffic Manager pour le routage du trafic basé sur DNS, et tester des scénarios de basculement.

## Étapes Suivies

### 1. Déploiement de l'Azure Load Balancer

#### Explication
Azure Load Balancer distribue le trafic réseau entrant vers plusieurs machines virtuelles pour assurer une haute disponibilité et une répartition de la charge.

#### Commandes / Étapes
- Accédez au **Portail Azure**.
- Créez une ressource **Load Balancer** en fournissant les détails requis (nom, type, région, groupe de ressources).
- Configurez le Frontend IP avec une adresse IP publique.
- Créez des **Back-end Pools** pour inclure les VMs que vous souhaitez équilibrer.

#### Capture d'écran
![Uploading image.png…]()


### 2. Configuration des Sondes de Santé et des Règles de Répartition de Charge

#### Explication
Les sondes de santé vérifient la disponibilité des instances en arrière-plan, tandis que les règles de répartition de charge déterminent comment le trafic est dirigé.

#### Commandes / Étapes
- Accédez à **Health probes** dans votre Load Balancer.
- Créez une sonde de santé de type `TCP` sur le port `80`.
- Créez une règle de répartition de charge pour diriger le trafic entrant vers les VM.

#### Capture d'écran
![Configuration Sondes de Santé](./screenshots/load-balancer-health-probes.png)

### 3. Configuration d'Azure Traffic Manager

#### Explication
Azure Traffic Manager permet de gérer le routage du trafic DNS entre plusieurs points de terminaison pour optimiser la latence et assurer la continuité des services.

#### Commandes / Étapes
- Créez un **Traffic Manager profile** en choisissant le type de méthode de routage.
- Ajoutez des points de terminaison en sélectionnant votre Load Balancer.

#### Capture d'écran
![Configuration Azure Traffic Manager](./screenshots/traffic-manager-configuration.png)

### 4. Test des Scénarios de Basculement

#### Explication
Il est crucial de vérifier comment le système réagit lorsque certaines instances deviennent indisponibles.

#### Commandes / Étapes
- Arrêtez une des VMs dans le backend pool.
- Testez l'accès à votre Load Balancer pour vérifier que le trafic est redirigé vers les instances restantes.
- Surveillez les résultats via le Portail Azure.

#### Capture d'écran
![Test de Basculement](./screenshots/failover-test.png)

### Conclusion
Ce laboratoire a permis de comprendre le déploiement et la configuration d'Azure Load Balancer et Azure Traffic Manager pour assurer la haute disponibilité des applications. J'ai acquis des compétences sur la gestion du routage du trafic et le test de scénarios de basculement pour garantir la continuité des services.
