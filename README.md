##  现在包都是 v2的，上传个 v3的。

#### 开始开始

```
    <?php
    
       $info = config('opensearch');
        //开启调试模式
        $options = array('debug' => false);

        $client = new \OpenSearch\Client\OpenSearchClient($info['app_id'], $info['app_secret'], $info['endPoint'], $options);
        // 实例化一个搜索类
        $searchClient = new \OpenSearch\Client\SearchClient($client);
        // 实例化一个搜索参数类
        $params = new \OpenSearch\Util\SearchParamsBuilder();
        //设置config子句的hit值
        $params->setHits(20);
 
        $params->setAppName('seo');
       // 指定搜索关键词
        $params->setQuery("default:'{$this->tag}'");
       // 指定返回的搜索结果的格式为json.gitignore
        $params->setFormat("fulljson");

        // 执行搜索，获取搜索结果
        $ret = $searchClient->execute($params->build());

        $result = json_decode($ret->result,true)['result']['items'];

```
