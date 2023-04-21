const searchInput = document.getElementById("search-field");
const output = document.getElementById("result");

searchInput.addEventListener("keyup", function(event) {
  if (event.keyCode === 13) {
    const inputValue = searchInput.value.toUpperCase();
    fetch('https://data.iana.org/TLD/tlds-alpha-by-domain.txt')
      .then(response => response.text())
      .then(data => {
        const domains = data.trim().split('\n');
        let matchFound = false;
        let domainList = document.createElement("ul");
        for (let i = 0; i < domains.length; i++) {
          const domainLength = domains[i].length;
          if (inputValue.slice(-domainLength) === domains[i]) {
            let domainItem = document.createElement("ul");
            domainItem.textContent = `${inputValue.slice(0, -domainLength)}.${domains[i]}`.toLowerCase();
            domainList.appendChild(domainItem);
            matchFound = true;
          }
        }
        if (!matchFound) {
          console.log(`No match.`);
          output.textContent = `Sorry, your name doesn't have a suitable suffix which can be replaced with a domain.`;
        } else {
          output.textContent = "";
          output.appendChild(domainList);
        }
      });
  }
});
