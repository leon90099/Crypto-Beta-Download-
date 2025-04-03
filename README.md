# Crypto-Beta-Download-Hauptanwendungscode (Python / Flask Backend)

from flask import Flask, jsonify, request

app = Flask(name)

Beispiel: Benutzerkonten (Datenbankersatz für Demo)

users = { "user1": {"balance": 10, "mined": 5}, "user2": {"balance": 20, "mined": 10} }

@app.route("/balance/<username>", methods=["GET"]) def get_balance(username): if username in users: return jsonify(users[username]) return jsonify({"error": "User not found"}), 404

if name == "main": app.run(debug=True)

Frontend (React Code) für die GUI

import React from "react";

const App = () => { const [username, setUsername] = React.useState(""); const [balance, setBalance] = React.useState(null);

const fetchBalance = async () => {
    const response = await fetch(`/balance/${username}`);
    const data = await response.json();
    setBalance(data);
};

return (
    <div>
        <h1>Krypto Mining App</h1>
        <input
            type="text"
            placeholder="Benutzername"
            value={username}
            onChange={(e) => setUsername(e.target.value)}
        />
        <button onClick={fetchBalance}>Kontostand abrufen</button>
        {balance && (
            <div>
                <p>Guthaben: {balance.balance}</p>
                <p>Mining-Ertrag: {balance.mined}</p>
            </div>
        )}
    </div>
);

};

export default App;

