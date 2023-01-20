String[] keywordList = {"apache spark", "Apache Spark", "Apache Pinot", "flink", "Flink", "Apache Flink", "kafka", "Kafka", "Apache Kafka", "pulsar", "Pulsar", "datapipeline", "real-time", "real-time streaming", "


continue
"StreamNative", "Confluent", "RedPandaData", "Apache Pulsar", "streaming", "Streaming", "big data", "Big Data"};
Pattern wordsRe = Pattern.compile(String.join("|", keywordList));

Copy code
    // class Listener
    // {
    //     public void onUpdate(Status status) {
    //         if (wordsRe.matcher(status.getContent()).find()) {
    //             JSONObject json_string = new JSONObject();
    //             json_string.put("language", status.getLanguage());
    //             json_string.put("created_at", status.getCreatedAt().toString());
    //             json_string.put("ts", System.currentTimeMillis() / 1000);
    //             json_string.put("uuid", UUID.randomUUID().toString());
    //             json_string.put("uri", status.getUri());
    //             json_string.put("url", status.getUrl());
    //             json_string.put("favourites_count", status.getFavouritesCount());
    //             json_string.put("replies_count", status.getRepliesCount());
    //             json_string.put("reblogs_count", status.getReblogsCount());
    //             json_string.put("content", status.getContent());
    //             json_string.put("username", status.getUsername());
    //             json_string.put("accountname", status.getAccountName());
    //             json_string.put("displayname", status.getDisplayName());
    //             json_string.put("note", status.getNote());
    //             json_string.put("followers_count", status.getFollowersCount());
    //             json_string.put("statuses_count", status.getStatusesCount());

    //             // Pulsar
    //             // Producer<mastodondata> pulsarProducer = pulsarClient.newProducer(Schema.AVRO(mastodondata.class))
    //             //    .topic("persistent://public/default/mastodon")
    //             //    .create();
    //             // pulsarProducer.send(mastodonRec);

    //             // MQTT
    //             client.publish("persistent://public/default/mqtt-2", json_string.toString().getBytes(), 0, true);

    //             // AMQP/RabbitMQ
    //             // channel.basicPublish("", "amqp-enviro", null, json_string.toString().getBytes("UTF-8"));

    //             // Kafka
    //             // producer.send(new ProducerRecord<>("rp4-kafka-1", json_string.toString()));
    //         }
    //     }
    // }
}
}

Copy code
Keep in mind that the above code is just an example and may not run as is, as the specific Java libraries and classes that replace the original Python libraries may have different methods and properties, and the actual code will depend on the specific requirements of the application.


