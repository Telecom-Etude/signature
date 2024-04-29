<script>
  let currentValue = {
    nom: "",
    prenom: "",
    poste: "",
    phone: "",
    mail: "",
    feminine: false,
  };
  let pre;
  let logoUrl = "https://telecom-etude.github.io/signature/logo_telecom_etude.png";
</script>

<main>
  <div class="header"><p>Telecom etude</p></div>
  <div class="form">
    <div>
      <br />
      <label for="nom">Nom</label>
      <input bind:value={currentValue.nom} name="nom" />
      <br />
      <label for="prenom">Prenom</label>
      <input bind:value={currentValue.prenom} name="prenom" />
      <br />
      <label for="phone">Tel</label>
      <input bind:value={currentValue.phone} name="phone" type="tel" />
      <br />
      <label for="poste">Poste</label>
      <input bind:value={currentValue.poste} name="poste" />
      <br />
      <label for="mail">Email</label>
      <input bind:value={currentValue.mail} name="mail" type="email" />
      <br />
      <label class="label" for="feminine">Féminin</label>
      <input
        bind:checked={currentValue.feminine}
        name="feminine"
        type="checkbox"
      />
    </div>
    <br />
    <button
      on:click={() => {
        debugger;
        navigator.clipboard.writeText(pre.value);
      }}>Copy</button
    >
  </div>
  <div class="result">
    <div>
      <hr />
      <table
        width="100%"
        style="font-family: Helvetica, Arial, serif; font-size: 13px; color: rgb(153, 153, 153); line-height: 1.5;"
      >
        <tbody>
          <td width="140px" align="center">
            <a href="https://telecom-etude.fr/" rel="noopener" target="_blank">
              <img
                width="100"
                height="100"
                src={logoUrl}
                alt="Logo Telecom Etude"
              />
            </a>
          </td>

          <td>
            <span
              style="color: rgb(0, 0, 0); line-height: 2.2; font-weight: 600;"
              >{currentValue.prenom} {currentValue.nom}</span
            ><br />

            Élève ingénieur{currentValue.feminine ? "e" : ""} à
            <a
              href="https://www.telecom-paris.fr/"
              style="color: #E54540"
              target="_blank">Télécom Paris</a
            ><br />

            {currentValue.poste} à
            <a
              href="https://telecom-etude.fr/"
              style="color: #E54540"
              target="_blank">Telecom Etude</a
            ><br />

            <a
              href="mailto:{currentValue.mail}"
              target="_blank"
              style="color : #E54540">{currentValue.mail}</a
            ><br />

            <a style="color:#E54540" href="tel:{currentValue.phone}">
              <span>{currentValue.phone}</span>
            </a>
          </td>
        </tbody>
      </table>
      <hr />
    </div>
    <textarea bind:this={pre}>
      {`
<div>
	<hr />
	<table
		width="100%"
		style="font-family: Helvetica, Arial, serif; font-size: 13px; color: rgb(153, 153, 153); line-height: 1.5;">
		<tbody>
			<td width="140px" align="center">
				<a href="https://telecom-etude.fr/" rel="noopener" target="_blank">
					<img
						width="100"
						height="100"
						src="${logoUrl}"
						alt="Logo Telecom Etude"
					/>
				</a>
			</td>
			<td>
				<span style="color: rgb(0, 0, 0); line-height: 2.2; font-weight: 600;">
					${currentValue.prenom} ${currentValue.nom}</span><br />
				Élève ingénieur${currentValue.feminine ? "e" : ""} à
				<a href="https://www.telecom-paris.fr/" style="color:#E54540" target="_blank">Télécom Paris</a><br />
				${currentValue.poste} à
				<a href="https://telecom-etude.fr/" style="color:#E54540" target="_blank">Telecom Etude</a><br />
				<a href="mailto:${currentValue.mail}" target="_blank" style="color:#E54540">
					${currentValue.mail}
				</a><br />
				<a style="color:#E54540" href="tel:${currentValue.phone}">
					<span>${currentValue.phone}</span>
				</a>
			</td>
		</tbody>
	</table>
	<hr />
</div>`}
    </textarea>
  </div>
</main>

<style>
  .header {
    text-align: center;
    background: rgb(253, 131, 52);
    background: linear-gradient(
      145deg,
      rgba(253, 131, 52, 1) 0%,
      rgba(224, 59, 66, 1) 35%,
      rgba(213, 31, 72, 1) 100%
    );
    color: white;
  }
  .header > p {
    font-family: "Helvetica";
    font-weight: bold;
    font-size: 40px;
    margin: 0px;
    padding: 10px;
  }
  .label {
    display: inline;
  }
  .result > :nth-child(2) {
    right: 0;
  }
  .result {
    display: flex;
    flex-direction: row;
  }
  .result > * {
    flex: 0.5;
    vertical-align: middle;
    margin: 20px;
  }
  textarea {
    font-size: 8px;
    text-align: left;
    height: 300px;
    width: calc(100% - 40px);
    border: 2px solid black;
  }
  .form {
    text-align: center;
  }
  main {
    margin: 0 auto;
  }

  @media screen and (max-width: 720px) {
    .result {
      display: block;
    }
  }
</style>
