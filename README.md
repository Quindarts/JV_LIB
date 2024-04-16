# JV_LIB

# Setup POM.XML
<dependencies>
		<!-- https://mvnrepository.com/artifact/org.hibernate.orm/hibernate-core -->
		<dependency>
			<groupId>org.hibernate.orm</groupId>
			<artifactId>hibernate-core</artifactId>
			<version>6.4.4.Final</version>
		</dependency>
		<!--
		https://mvnrepository.com/artifact/com.microsoft.sqlserver/mssql-jdbc -->
		<dependency>
			<groupId>com.microsoft.sqlserver</groupId>
			<artifactId>mssql-jdbc</artifactId>
			<version>12.3.0.jre17-preview</version>
		</dependency>
</dependencies>

# Setup Persistence.xml
	<properties>
			<property name="jakarta.persistence.jdbc.driver"
				value="com.microsoft.sqlserver.jdbc.SQLServerDriver" />
			<property name="jakarta.persistence.jdbc.dialect"
				value="org.hibernate.dialect.SQLServerDialect" />
			<property name="hibernate.connection.url"
				value="jdbc:sqlserver://localhost:1433;databaseName=schooldb;trustServerCertificate=true;encrypt=true;" />
			<property name="hibernate.connection.username" value="sa" />
			<property name="hibernate.connection.password"
				value="sapassword" />
			<property name="hibernate.hbm2ddl.auto" value="update" />
			<property name="hibernate.show_sql" value="true" />
			<property name="hibernate.format_sql" value="true" />
		</properties>

  
  <!--
private static final Gson GSON = new GsonBuilder().create();

	public static Driver getDriver() {
		return GraphDatabase.driver("neo4j://localhost:7687", AuthTokens.basic("neo4j", "12345678"));
	}

	public static <T> T nodeToPOPJO(Node node, Class<T> clazz) {
		Map<String, Object> map = node.asMap();
		String json = GSON.toJson(map);
		T obj = GSON.fromJson(json, clazz);
		return obj;

	};

	public static <T> Map<String, Object> getProp(T t) {
		String json = GSON.toJson(t);
		Map<String, Object> map = GSON.fromJson(json, new TypeToken<Map<String, Object>>() {
		});
		return map;
	}

-->
<!-- https://mvnrepository.com/artifact/com.google.code.gson/gson -->
		<dependency>
			<groupId>com.google.code.gson</groupId>
			<artifactId>gson</artifactId>
			<version>2.10.1</version>
		</dependency>
		<!--
		https://mvnrepository.com/artifact/org.neo4j.driver/neo4j-java-driver -->
		<dependency>
			<groupId>org.neo4j.driver</groupId>
			<artifactId>neo4j-java-driver</artifactId>
			<version>5.18.0</version>
		</dependency>
		<!--
		https://mvnrepository.com/artifact/org.junit.jupiter/junit-jupiter-api -->
		<dependency>
			<groupId>org.junit.jupiter</groupId>
			<artifactId>junit-jupiter-api</artifactId>
			<version>5.10.2</version>
			<scope>test</scope>
		</dependency>

