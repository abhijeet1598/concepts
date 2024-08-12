# HTML & CSS Concepts

## HTML (HyperText Markup Language)

### 1. Basic Structure

- **Doctype**: Defines the document type and version of HTML. Example: `<!DOCTYPE html>`.
- **HTML Element**: The root element (`<html>`) that contains the entire document.
- **Head Section**: Includes metadata, title, and links to stylesheets or scripts.
- **Body Section**: Contains the content to be displayed on the webpage.

### 2. Common HTML Tags

- **Headings**: `<h1>` to `<h6>` for different levels of headings.
- **Paragraph**: `<p>` for paragraphs.
- **Links**: `<a>` for hyperlinks.
- **Images**: `<img>` for embedding images.
- **Lists**: `<ul>` for unordered lists, `<ol>` for ordered lists, and `<li>` for list items.
- **Tables**: `<table>`, `<tr>`, `<td>`, `<th>` for creating tables.
- **Forms**: `<form>`, `<input>`, `<button>`, `<select>`, etc., for creating forms.

### 3. Attributes

- **Class**: Specifies one or more class names for an element (`class="classname"`).
- **ID**: Defines a unique ID for an element (`id="uniqueid"`).
- **Src**: Specifies the source of an image (`src="image.jpg"`).
- **Href**: Specifies the URL of a link (`href="https://example.com"`).
- **Alt**: Provides alternative text for images (`alt="description"`).

### 4. Meta Tags

- **Meta Tag**: Provides metadata about the HTML document, which is used by browsers and search engines. Meta tags are placed inside the `<head>` section.
  - **Viewport**: Controls the layout on mobile browsers.
  - **Description**: Provides a summary of the page content for search engines. This is useful for search engine optimization.
  - **Keywords**: Lists keywords relevant to the page for search engines. This is useful for search engine optimization.
  - **Author**: Specifies the author of the document.

### 5. Charset and Encoding

- **Charset**: Specifies the character encoding used in the document. UTF-8 is the most commonly used encoding, supporting a wide range of characters.
  - **UTF-8**: A universal character set that includes almost all characters from all languages. The charset is specified using the meta tag (`<meta charset="UTF-8">`).

### 6. Unicode Encoding

- **Unicode**: A universal character encoding standard that assigns a unique number (code point) to every character in every language, symbol, or script. It aims to cover all the writing systems of the world.
  - **UTF-8**: A variable-length character encoding for Unicode, capable of encoding all possible characters (code points) in Unicode. It's backward compatible with ASCII and is widely used on the web.
  - **UTF-16**: Another Unicode encoding capable of encoding over a million characters. It uses one or two 16-bit code units to encode characters.

### 7. Comments

- **HTML Comments**: Used to add notes or explanations in the code that are not displayed in the browser. They help in documenting the code (`<!-- This is a comment -->`).

### 8. Semantic HTML

- **Semantic Elements**: Tags that convey meaning about the content inside them, improving accessibility and SEO.
  - **Examples**: `<header>`, `<footer>`, `<article>`, `<section>`, `<nav>`, `<aside>`.

## CSS (Cascading Style Sheets)

### 1. Syntax

- **Selectors**: Target HTML elements to apply styles (e.g., `p`, `.classname`, `#id`).
- **Properties**: Define what you want to style (e.g., `color`, `font-size`, `margin`).
- **Values**: Specify how the properties should be styled (e.g., `red`, `16px`, `10px`).

### 2. Types of CSS

- **Inline CSS**: Applied directly within HTML elements using the `style` attribute.
- **Internal CSS**: Placed within a `<style>` tag inside the `<head>` section of the HTML document.
- **External CSS**: Written in a separate `.css` file and linked to the HTML document using the `<link>` tag.

### 3. CSS Box Model

- **Content**: The actual content of the element (text, image, etc.).
- **Padding**: Clears space inside the element, around the content.
- **Border**: Surrounds the padding (if any) and content.
- **Margin**: Clears space outside the element, around the border.

### 4. Positioning

- **Static**: Default positioning of elements.
- **Relative**: Positioned relative to it's normal position.
- **Absolute**: Positioned relative to it's nearest positioned ancestor.
- **Fixed**: Positioned relative to the browser window.
- **Sticky**: It is positioned relative until a given offset position is met in the viewport - then it "sticks" in place (like position:fixed).

### 5. Flexbox

- **Flex Container**: The parent element with `display: flex`.
- **Flex Items**: The children of the flex container.
- **Properties**:
  - `flex-direction`: Defines the direction of the flex items (row or column).
  - `justify-content`: Aligns items horizontally (vertical if flex direction is column).
  - `align-items`: Aligns items vertically (horizontally if flex direction is column).

### 6. Grid

- **Grid Container**: The parent element with `display: grid`.
- **Grid Items**: The children of the grid container.
- **Properties**:
  - `grid-template-columns`: Defines the number and size of columns.
  - `grid-template-rows`: Defines the number and size of rows.
  - `grid-gap`: Specifies the gap between rows and columns.

## Best Practices

- **Use Semantic HTML**: Enhance accessibility and SEO by using tags like `<header>`, `<footer>`, `<article>`, etc.
- **Keep CSS Organized**: Use comments, consistent naming conventions, and separate concerns with different CSS files.
- **Responsive Design**: Ensure your website looks good on all devices using media queries, flexible layouts, and responsive units like `%`, `em`, and `rem`.
