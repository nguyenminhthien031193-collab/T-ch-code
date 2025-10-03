let players = [
    { name: "Vũ Hoàng", scores: [0, 2, 0, 1] },
    { name: "Minh Đức", scores: [0, 3, 0, 1] },
    { name: "Bambi", scores: [0, 2, 0, 2] }
];

const renderTable = () => {
    const tableBody = document.getElementById('scoreTable').querySelector('tbody');
    tableBody.innerHTML = ''; // Xóa nội dung cũ

    players.forEach((player, playerIndex) => {
        const row = tableBody.insertRow();
        row.insertCell().textContent = player.name; // Cột Tên

        player.scores.forEach((score, scoreIndex) => {
            const cell = row.insertCell();
            cell.textContent = score; // Hiển thị điểm

            // Thêm nút "Tích" (O) kế bên số điểm
            const btn = document.createElement('button');
            btn.textContent = 'O'; // Hoặc biểu tượng tròn CSS
            btn.className = 'score-increment-btn';
            
            // Hàm xử lý sự kiện khi nhấn
            btn.onclick = () => handleScoreIncrease(playerIndex, scoreIndex);
            
            cell.prepend(btn); // Chèn nút vào đầu ô
        });
    });
}

const handleScoreIncrease = (playerIndex, scoreIndex) => {
    // Tăng điểm tại vị trí tương ứng
    players[playerIndex].scores[scoreIndex]++;
    
    // Render lại toàn bộ bảng để cập nhật giao diện
    renderTable();
    
    // Lưu ý: Với cách dùng nút (Button), nó đã sẵn sàng để tích lần tiếp theo mà KHÔNG cần thao tác "reset" nào.
};

// Khởi tạo ứng dụng
document.addEventListener('DOMContentLoaded', renderTable);
