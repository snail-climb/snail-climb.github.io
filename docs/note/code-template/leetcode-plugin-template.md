## leetcode-plugin-template

### 1. Code FileName

```java
P${question.frontendQuestionId}$!velocityTool.camelCaseName(${question.titleSlug})
```

### 2. Code Template

```java
${question.content}
package leetcode.editor.cn;
// java:${question.title}
public class P${question.frontendQuestionId}$!velocityTool.camelCaseName(${question.titleSlug}) {

	public static void main(String[] args) {
		Solution solution = new P${question.frontendQuestionId}$!velocityTool.camelCaseName(${question.titleSlug})().new Solution();
		// TO TEST
	}

	${question.code}
}

```

