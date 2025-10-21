# 🚀 TP5 - Application Spring Boot avec JPA

[![Java](https://img.shields.io/badge/Java-17-orange.svg)](https://openjdk.java.net/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-2.7.0-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Hibernate](https://img.shields.io/badge/Hibernate-5.6.12-blue.svg)](https://hibernate.org/)
[![Maven](https://img.shields.io/badge/Maven-3.9.5-red.svg)](https://maven.apache.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 📋 Description

Application Spring Boot complète avec :
- **Entités JPA** : Product et Category avec relations @ManyToOne/@OneToMany
- **DAOs** : Implémentation avec Hibernate et Spring
- **Contrôleurs REST** : API pour gérer les produits et catégories
- **Tests unitaires** : JUnit 5 avec base de données H2
- **Configuration IntelliJ** : Prêt pour le développement

## 🏗️ Architecture

```
src/
├── main/
│   ├── java/
│   │   ├── entities/          # 📊 Entités JPA (Product, Category)
│   │   ├── dao/               # 🔌 Interfaces DAO
│   │   ├── metier/            # ⚙️ Implémentations DAO
│   │   ├── Controller/        # 🌐 Contrôleurs REST
│   │   └── util/              # 🔧 Configuration Hibernate
│   ├── resources/
│   │   └── application.properties  # ⚙️ Configuration
│   └── webapp/                # 🌐 Ressources web
└── test/
    ├── java/                  # 🧪 Tests unitaires
    └── resources/             # 🧪 Configuration tests
```

## 🚀 Démarrage rapide

### Prérequis
- Java 17+
- Maven 3.6+
- IntelliJ IDEA (recommandé)

### 1. Cloner le repository
```bash
git clone https://github.com/ghaliel/TP5.git
cd TP5
```

### 2. Compiler le projet
```bash
mvn clean compile
```

### 3. Lancer les tests
```bash
mvn test
```

### 4. Démarrer l'application
```bash
mvn spring-boot:run
```

### 5. Tester l'application
- **Test de base** : http://localhost:8080/test
- **API Catégories** : http://localhost:8080/categories
- **API Produits** : http://localhost:8080/api/products

## 🧪 Tests

### Lancer tous les tests
```bash
mvn test
```

### Tests disponibles
- ✅ Tests unitaires des entités
- ✅ Tests d'intégration Spring Boot
- ✅ Tests avec base de données H2 en mémoire

## 🗄️ Base de données

### Production
- **MySQL** (configuration dans `application.properties`)
- URL: `jdbc:mysql://localhost:3306/basee`

### Tests
- **H2** en mémoire (configuration automatique)
- Tables créées automatiquement

## 🔧 Configuration IntelliJ IDEA

### 1. Ouvrir le projet
- File → Open → Sélectionner le dossier TP5
- IntelliJ détectera automatiquement le projet Maven

### 2. Configuration JDK
- File → Project Structure → Project
- Project SDK: Java 17
- Project language level: 17

### 3. Run Configurations
Le projet inclut des configurations prêtes :
- **Application** : Lance l'application Spring Boot
- **All Tests** : Exécute tous les tests

### 4. Lancer l'application
- Clic droit sur `Application.java` → Run 'Application'
- Ou Run → Application

## 📦 Dépendances principales

```xml
<dependencies>
    <!-- Spring Boot -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
        <version>2.7.0</version>
    </dependency>
    
    <!-- Spring Data JPA -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
        <version>2.7.0</version>
    </dependency>
    
    <!-- Hibernate -->
    <dependency>
        <groupId>org.hibernate</groupId>
        <artifactId>hibernate-core</artifactId>
        <version>5.6.12.Final</version>
    </dependency>
    
    <!-- MySQL -->
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>8.0.29</version>
    </dependency>
    
    <!-- H2 Database (tests) -->
    <dependency>
        <groupId>com.h2database</groupId>
        <artifactId>h2</artifactId>
        <version>2.1.214</version>
        <scope>test</scope>
    </dependency>
</dependencies>
```

## 🌐 API Endpoints

| Méthode | Endpoint | Description |
|---------|----------|-------------|
| GET | `/test` | Test de base de l'application |
| GET | `/categories` | Liste toutes les catégories |
| GET | `/api/products` | Liste tous les produits |
| POST | `/products/save` | Créer un nouveau produit |
| GET | `/products/new` | Formulaire de création |

## 🏛️ Entités JPA

### Product
```java
@Entity
public class Product {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;
    private String name;
    private double price;
    
    @ManyToOne
    @JoinColumn(name = "category_id")
    private Category category;
}
```

### Category
```java
@Entity
@Table(name = "categories")
public class Category {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    
    @OneToMany(mappedBy = "category", cascade = CascadeType.ALL)
    private List<Product> products;
}
```

## 🔧 Commandes Maven utiles

```bash
# Compiler
mvn clean compile

# Lancer les tests
mvn test

# Lancer l'application
mvn spring-boot:run

# Package
mvn clean package

# Installer les dépendances
mvn clean install
```

## 📚 Technologies utilisées

- **Java 17** - Langage de programmation
- **Spring Boot 2.7.0** - Framework principal
- **Spring Data JPA** - Persistance des données
- **Hibernate 5.6.12** - ORM
- **Maven 3.9.5** - Gestion des dépendances
- **JUnit 5** - Tests unitaires
- **H2 Database** - Base de données pour les tests
- **MySQL** - Base de données de production
- **IntelliJ IDEA** - IDE de développement

## 🤝 Contribution

1. Fork le projet
2. Créer une branche feature (`git checkout -b feature/AmazingFeature`)
3. Commit les changements (`git commit -m 'Add some AmazingFeature'`)
4. Push vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrir une Pull Request

## 📄 Licence

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

## 👨‍💻 Auteur

**ghaliel** - [GitHub](https://github.com/ghaliel)

## 🙏 Remerciements

- Spring Boot Team
- Hibernate Team
- IntelliJ IDEA Team
- Maven Team

---

⭐ N'hésitez pas à donner une étoile si ce projet vous a aidé !
