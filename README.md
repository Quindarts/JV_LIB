# JV_LIB

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
  private static final Gson GSON = new GsonBuilder().create();
//
//	public static Driver getDriver() {
//		return GraphDatabase.driver("neo4j://localhost:7687", AuthTokens.basic("neo4j", "12345678"));
//	}
//
//	public static <T> T nodeToPOPJO(Node node, Class<T> clazz) {
//		Map<String, Object> map = node.asMap();
//		String json = GSON.toJson(map);
//		T obj = GSON.fromJson(json, clazz);
//		return obj;
//
//	};
//
//	public static <T> Map<String, Object> getProp(T t) {
//		String json = GSON.toJson(t);
//		Map<String, Object> map = GSON.fromJson(json, new TypeToken<Map<String, Object>>() {
//		});
//		return map;
//	}
