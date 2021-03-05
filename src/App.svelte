<script>
  import { jsPDF } from "jspdf";
  import "./QETonyFlores-normal";
  let text = "";
  let loading = false;
  let fontSize = 16;
  let fontColor = "#202020";
  const doc = new jsPDF();

  function handleClick() {
    if (text.length > 0) {
      loading = true;
      doc.setFontSize(parseInt(fontSize));
      doc.setFont("QETonyFlores");
      doc.rect(
        10,
        10,
        doc.internal.pageSize.width - 20,
        doc.internal.pageSize.height - 20,
        "S"
      );
      doc.setTextColor(fontColor.trim());
      doc.text(
        `
    ${text}
    `,
        13,
        10
      );
      loading = false;
      doc.save("a4.pdf");
    }
  }
</script>

<main>
  <div class="navbar">
    <p>Assign/me (Beta)</p>
    <a href="https://github.com/Manitej66"> <img src="github.png" alt="" /></a>
  </div>
  <textarea
    bind:value={text}
    class="main-area"
    placeholder="type or paste the text to convert here"
  />
  <p class="text">Customize</p>
  <div class="customize">
    <div>
      <p>Text size</p>
      <input type="text" bind:value={fontSize} />
    </div>
    <div>
      <p>Text color</p>
      <input type="text" bind:value={fontColor} />
    </div>
  </div>
  <button disabled={loading} class="btn" on:click={handleClick}
    >{loading ? "Please wait.." : "Download PDF"}</button
  >
  >
</main>

<style>
  .navbar {
    background-color: #7868e6;
    padding: 4px;
    width: 100%;
    display: flex;
    justify-content: space-around;
    align-items: center;
  }
  .navbar > p {
    font-weight: 700;
    font-size: 18px;
    color: #fff;
  }
  .main-area {
    width: 90%;
    display: block;
    margin: 20px auto;
    min-height: 25vh;
    max-height: 30vh;
  }
  .customize {
    width: 90%;
    display: flex;
    margin: 0 auto;
    border: 1px solid #ccc;
    flex-direction: column;
    align-items: center;
  }
  .text {
    color: black;
    font-size: 20px;
    text-align: center;
  }
  .btn {
    margin: 20px auto;
    display: block;
    background-color: #7868e6;
    color: #fff;
    padding: 12px 20px;
    border: none;
    font-weight: 700;
    width: 50%;
  }
</style>
