# ECC_2025-1_BackEnd-StringBoot3_Chap9-11
--------------------------------------------
9장
CREATE TABLE 테이블명 (
	속성명1 자료형,
	속성명2 자료형,
	속성명3 자료형,
	PRIMARY KEY (기본키)
);

INSERT
INTO
	테이블명
	(속성명1, 속성명2, 속성명3, …)
VALUES
	(값1, 값2, 값3, …);

 SELECT
	속성명1, 속성명2, 속성명3
FROM
	테이블명
WHERE
	조건;

 SUPDATE
	테이블명
SET
	속성명=변경할 값
WHERE
	조건;

 DELETE
	[FROM] 
테이블명
	WHERE
조건;
-------------------------------------
10장
fetch('https://jsonplaceholder.typicode.com/posts/1')
  .then((response) => response.json())
  .then((json) => console.log(json));

  fetch('https://jsonplaceholder.typicode.com/posts')
  .then((response) => response.json())
  .then((json) => console.log(json));

  fetch('https://jsonplaceholder.typicode.com/posts', {
  method: 'POST',
  body: JSON.stringify({
    title: 'foo',
    body: 'bar',
    userId: 1,
  }),
  headers: {
    'Content-type': 'application/json; charset=UTF-8',
  },
})
  .then((response) => response.json())
  .then((json) => console.log(json));

  fetch('https://jsonplaceholder.typicode.com/posts/1', {
  method: 'PUT',
  body: JSON.stringify({
    id: 1,
    title: 'foo',
    body: 'bar',
    userId: 1,
  }),
  headers: {
    'Content-type': 'application/json; charset=UTF-8',
  },
})
  .then((response) => response.json())
  .then((json) => console.log(json));

  fetch('https://jsonplaceholder.typicode.com/posts/1', {
  method: 'PATCH',
  body: JSON.stringify({
    title: 'foo',
  }),

  fetch('https://jsonplaceholder.typicode.com/posts/1', {
  method: 'DELETE',
});
-----------------------------------------0
11장
package com.example.firstproject.api;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class FirstApiController {
    @GetMapping("/api/hello")
    public String hello(){
        return "hello world";
    }
}

package com.example.firstproject.api;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class FirstApiController {
    @GetMapping("/hi")
    public String niceMeetYou(Model model){
    mpdel.addAttribute("username", "hongpark");
        return "greetings"; //뷰 페이지 반환
    }
}


package com.example.firstproject.api;

import com.example.firstproject.entity.Article;
import com.example.firstproject.repository.ArticleRepository;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;

import java.util.List;

public class ArticleApiController {
    @Autowired
    private ArticleRepository articleRepository;

    @GetMapping("/api/articles")
    public List<Article> index() { 
        return articleRepository.findAll();
    }

}

@PostMapping("/api/articles")
    public Article create(ArticleForm dto) {
        Article article = dto.toEntity();
        return articleRepository.save(article);
    }

    @PatchMapping("/api/articles/{id}") 
    public Article update(@PathVariable Long id, 
    @RequestBody ArticleForm dto) {
    Article article = dto.toEntity();
	log.info("id: {}, article: {}", id, article.toString());
    }

     Article target = articleRepository.findById(id).orElse(null);

        if (target == null || id != article.getId()) {
            log.info("잘못된 요청! id: {}, article: {}", id, article.toString());
            return ResponseEntity.status(HttpStatus.BAD_REQUEST).body(null);
        }
    }

        Article updated = articleRepository.save(article);
        return ResponseEntity.status(HttpStatus.OK).body(updated);

        target.patch(article); 
        Article updated = articleRepository.save(target); 
        return ResponseEntity.status(HttpStatus.OK).body(updated);
}


public void patch(Article article) {
if (article.title != null)
this.title = article.title;
if (article.content != null)
this.content = article.content;
}
