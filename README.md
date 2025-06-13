# Employee-Management-System// App.jsx

import React, { useState } from 'react';
import {
  BrowserRouter as Router,
  Routes,
  Route,
  useNavigate
} from 'react-router-dom';

function LoginScreen() {
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');
  const [error, setError] = useState('');
  const [showForgotPassword, setShowForgotPassword] = useState(false);
  const navigate = useNavigate();

  const handleLogin = () => {
    // Add more user types if needed
    if (
      (username === 'admin' && password === 'admin123') ||
      (username === 'Dhiraj' && password === 'Dhiraj@123')
    ) {
      navigate('/dashboard');
    } else {
      setError('Invalid username or password');
    }
  };

  const handleForgotPassword = () => {
    setShowForgotPassword(true);
  };

  return (
    <div
      style={{ backgroundColor: '#d3d3d3' }}
      className="min-h-screen flex items-center justify-center"
    >
      <div className="w-full max-w-md bg-white rounded-lg shadow-md p-6">
        <div className="flex justify-center mb-4">
          <span className="text-gray-600 text-3xl">🔒</span>
        </div>
        <h2 className="text-2xl font-bold mb-4 text-center">
          KTCL Employee Login
        </h2>

        <input
          type="text"
          placeholder="Username/Login ID"
          className="w-full px-3 py-2 mb-4 border rounded text-sm"
          value={username}
          onChange={(e) => setUsername(e.target.value)}
        />

        <input
          type="password"
          placeholder="Password"
          className="w-full px-3 py-2 mb-4 border rounded text-sm"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
        />

        {error && <p className="text-red-500 mb-2 text-sm">{error}</p>}

        <button
          className="w-full bg-blue-600 text-white py-2 rounded mb-2 hover:bg-blue-700 text-sm"
          onClick={handleLogin}
        >
          Login
        </button>

        <button
          className="text-sm text-blue-600 hover:underline w-full"
          onClick={handleForgotPassword}
        >
          Forgot Password?
        </button>

        {showForgotPassword && (
          <div className="mt-4 text-sm text-gray-600">
            Please contact the Personnel Office:<br />
            📞 <strong>9226077948</strong> <br />
            📧 <strong>kadambapersonal@gmail.com</strong>
          </div>
        )}
      </div>
    </div>
  );
}

function Dashboard() {
  return (
    <div className="min-h-screen p-6 bg-gray-100">
      <h1 className="text-2xl font-bold mb-4">
        Welcome to KTCL Employee Dashboard
      </h1>
      <p className="text-sm text-gray-700">Dashboard content will be added here.</p>
    </div>
  );
}

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<LoginScreen />} />
        <Route path="/dashboard" element={<Dashboard />} />
      </Routes>
    </Router>
  );
}

export default App;
