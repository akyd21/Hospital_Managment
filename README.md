spring.application.name=hospitalManagement

# DB configuration (MySQL)
spring.datasource.url=jdbc:mysql://localhost:3306/hospitalDB
spring.datasource.username=root
spring.datasource.password=your_password

# MySQL Driver
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

server.servlet.context-path=/api/v1

# JPA / Hibernate
spring.jpa.hibernate.ddl-auto=create
spring.jpa.show-sql=true

# MySQL Dialect
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect

# Security config (optional)
# spring.security.user.name=anuj
# spring.security.user.password=pass

jwt.secretKey=asdfhads9f67as98dfyaisudhfa98s67dfy89aishudfuays89dfyasi8df7asdf87987g98a7sg986a89sdf7y