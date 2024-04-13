const generateTicket = () => {
  fetch('/generateTicket')
    .then(response => response.json())
    .then(data => {
      const ticketDiv = document.getElementById('ticket');
      ticketDiv.innerHTML = '';
      data.forEach(row => {
        const rowDiv = document.createElement('div');
        rowDiv.classList.add('row');
        row.forEach(number => {
          const cellDiv = document.createElement('div');
          cellDiv.classList.add('cell');
          cellDiv.textContent = number;
          rowDiv.appendChild(cellDiv);
        });
        ticketDiv.appendChild(rowDiv);
      });
    })
    .catch(error => console.error('Error:', error));
};

document.getElementById('generateBtn').addEventListener('click', generateTicket);
