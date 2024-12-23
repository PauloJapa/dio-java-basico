# Use uma imagem base com o JDK e Maven
FROM maven:3.8.5-openjdk-17-slim

# Defina o diretório de trabalho dentro do container
WORKDIR /app

# Copie os arquivos pom.xml e settings.xml (se tiver)
COPY ../app/pom.xml ../app/settings.xml ./

# Baixe as dependências (para aproveitar o cache de camadas do Docker)
RUN mvn dependency:go-offline

# Copie o código fonte (relativo à raiz do projeto)
COPY ../src ./src

# Construa a aplicação
RUN mvn package

# Comando para executar a aplicação (ajuste o nome do JAR)
CMD ["java", "-jar", "target/meu-aplicativo.jar"]

# Exponha a porta da aplicação (se necessário)
EXPOSE 8080