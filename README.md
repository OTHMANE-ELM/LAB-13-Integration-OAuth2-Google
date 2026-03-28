# 🔐 LAB 13 – Authentification OAuth2 avec Google & Spring Boot


## 📌 Objectif

Mettre en place une authentification SSO (Single Sign-On) avec Google dans une application Spring Boot, en utilisant le protocole **OAuth 2.0** et **OpenID Connect**.

L'utilisateur peut :
- Se connecter via son compte Google
- Accéder à une page de profil affichant son nom, email et photo
- Se déconnecter proprement

---

## 🛠️ Technologies utilisées

| Technologie | Version |
|---|---|
| Java | 25 (OpenJDK) |
| Spring Boot | 4.0.5 |
| Spring Security | 7.0.4 |
| Spring Security OAuth2 Client | 7.0.4 |
| Thymeleaf | 3.1.3 |
| Lombok | 1.18.44 |
| Maven | 3.x |
| Tomcat (embarqué) | 11.0.20 |

---

## 📁 Structure du projet

```
OAuth2-Google/
├── src/
│   ├── main/
│   │   ├── java/ma/fstg/security/
│   │   │   ├── OAuth2GoogleApplication.java     # Classe principale Spring Boot
│   │   │   ├── config/
│   │   │   │   └── SecurityConfig.java          # Configuration Spring Security
│   │   │   └── web/
│   │   │       └── HomeController.java          # Controller MVC (/, /profile)
│   │   └── resources/
│   │       ├── application.yml                  # Configuration OAuth2 + serveur
│   │       └── templates/
│   │           ├── index.html                   # Page d'accueil (login)
│   │           └── profil.html                  # Page de profil utilisateur
│   └── test/
│       └── java/ma/fstg/security/
│           └── OAuth2GoogleApplicationTests.java
└── pom.xml
```

---

## ⚙️ Configuration

### `application.yml`

```yaml
server:
  port: 8081

spring:
  security:
    oauth2:
      client:
        registration:
          google:
            client-id: TON_CLIENT_ID
            client-secret: TON_CLIENT_SECRET
            scope:
              - openid
              - profile
              - email
        provider:
          google:
            issuer-uri: https://accounts.google.com
```

---




## 🔄 Flux OAuth2

```
Utilisateur → /oauth2/authorization/google
           → Redirection vers Google (consentement)
           → Google rappelle : /login/oauth2/code/google
           → Spring Security valide le token
           → Redirection vers /profile
```

---
## Video Demo : 



https://github.com/user-attachments/assets/03dcae94-3312-4aa0-b620-e42ae2981b0c


