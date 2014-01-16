Installation
------------

Add to your project's Build.scala
    
    resolvers += "Sonatype snapshots" at "http://oss.sonatype.org/content/repositories/snapshots/",
    libraryDependencies ++= Seq(
        "com.github.klasu" %% "simple-dynamodb" % "0.1-SNAPSHOT"
    )

Usage
-----

    import simpledynamodb._

    object A extends DynamoDb {
      def table = db.table("TableName", "Credentials", "SecretKey")
      
      def query = {
        val resultFuture: Future[List[Map[String, String]]] = table.query("searchKey").perform
      }
      
      def store(values: Map[String, String]) = {
        table.store("Key", "Range", values)
      }
    }

