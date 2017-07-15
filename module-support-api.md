FORMAT: 1A
HOST: http://polls.apiblueprint.org/

# support

+ 2017年7月12日
    + API初始化

文章主题模块

## (POST)评论 [/comments]

+ Description
    + [MUST] Authenticated
    
+ Data
    + confId (long) - 
    + themeId (long) - 
    + topId (long) - 
    + replayId (long) -
    + reUserId (long) - 
    + content (string) - 评论内容
    + isAnonymous (int) - 
    + tagIds (array) - 

### 增加评论 [POST]

+ Request (application/json)

        {
            "data": {
                "confId": 1,
                "themeId": 1,
                "topId": 0,
                "replayId": 1,
                "reUserId": 1031,
                "content": "回复内容, 啊啊啊 专业",
                "isAnonymous": 0,
                "tagIds": [
                    1,
                    2
                ]
            }
        }

+ Response 201 (application/json)

    + Headers

            Location: /comments/2

    + Body

            {
                "data": {
                    "id": 2,
                    "type": "comments"
                }
            }
            
+ Response 204 (application/json)

+ Response 400 (application/json)

        {
            "errors": [
                {
                    "status": "400",
                    "code": "应用程序code编码",
                    "title": "Bad Request",
                    "detail": "错误信息描述"
                }
            ]
        }

## (GET)评论集合 [/comments/list?page[number]=1&page[size]=10&confId=1&themeId=1&topId=0]

### 查询评论集合 [GET]

+ Response 200 (application/json)

        {
            "meta": {
                "number": 1,
                "size": 5,
                "numberOfElements": 5,
                "last": false,
                "totalPages": 6,
                "sort": [
                    {
                        "direction": "DESC",
                        "property": "created",
                        "ignoreCase": false,
                        "nullHandling": "NATIVE",
                        "descending": true,
                        "ascending": false
                    }
                ],
                "first": true,
                "totalElements": 26
            },
            "links": {
                "self": "/api/comment/list?confId=1&themeId=1&topId=0&page[number]=1&page[size]=5",
                "first": "/api/comment/list?confId=1&themeId=1&topId=0&page[number]=1&page[size]=5",
                "next": "/api/comment/list?confId=1&themeId=1&topId=0&page[number]=2&page[size]=5",
                "last": "/api/comment/list?confId=1&themeId=1&topId=0&page[number]=6&page[size]=5"
            },
            "data": [
                {
                    "id": 51,
                    "enabled": 1,
                    "creator": 1031,
                    "created": "2017-06-06 16:16:35",
                    "themeId": 1,
                    "confId": 1,
                    "topId": 0,
                    "content": "hello word zyw",
                    "isAnonymous": 0,
                    "state": 0,
                    "praiseCount": 0,
                    "_praiseCount": 0,
                    "replayCount": 0,
                    "reComments": []
                },
                {
                    "id": 41,
                    "enabled": 1,
                    "creator": 1031,
                    "created": "2017-06-06 13:59:26",
                    "themeId": 1,
                    "confId": 1,
                    "topId": 0,
                    "content": "222hello word zyw",
                    "isAnonymous": 0,
                    "state": 0,
                    "praiseCount": 0,
                    "_praiseCount": 0,
                    "replayCount": 0,
                    "reComments": []
                }
            ]
        }
        
## (DELETE)评论 [/comments/{id}]

+ Description
    + [MUST] Authenticated
    + [MUST] 用户只能操作自己的资源

+ Parameters
    + id (long) - 评论ID

### 删除地址信息 [DELETE]

+ Response 200 (application/json)

+ Response 202 (application/json)

+ Response 204 (application/json)

+ Response 400 (application/json)

        {
            "errors": [
                {
                    "status": "400",
                    "code": "应用程序code编码",
                    "title": "Bad Request",
                    "detail": "错误信息描述"
                }
            ]
        }
        
## (GET)评论标签集合 [/commentConf/{id}]

+ Description
    + 

+ Parameters
    + id (long) - 

+ Response 200 (application/json)

        {
            "data": {
                "id": 1,
                "confName": "产品详情评论配置",
                "tags": [
                    {
                        "id": 1,
                        "tagName": "质量不错"
                    },
                    {
                        "id": 2,
                        "tagName": "222222222"
                    }
                ]
            }
        }



