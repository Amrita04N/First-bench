# First-bench
Assignment 1
 // Project structure:
src/
├── components/
│   ├── layout/
│   │   └── Navbar.jsx
│   ├── dashboard/
│   │   ├── ResultCard.jsx
│   │   ├── SubjectTags.jsx
│   │   ├── ResponseTime.jsx
│   │   ├── ApproachData.jsx
│   │   ├── AccuracyChart.jsx
│   │   └── TimeTaken.jsx
│   └── ui/
│       ├── Card.jsx
│       └── Button.jsx
├── styles/
│   └── globals.css
├── App.jsx
└── main.jsx

// First, install dependencies:
// npm create vite@latest firstbench-dashboard -- --template react
// cd firstbench-dashboard
// npm install
// npm install @radix-ui/react-slot class-variance-authority clsx lucide-react tailwindcss postcss autoprefixer recharts @radix-ui/react-icons

// tailwind.config.js
module.exports = {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {
      colors: {
        primary: '#6366f1',
        secondary: '#1e293b',
        accent: '#22c55e',
      }
    }
  },
  plugins: [],
}

// src/components/layout/Navbar.jsx
import React from 'react';
import { Home, Book, Users, Zap, BarChart2, PenTool, Bell } from 'lucide-react';

export const Navbar = () => {
  const navItems = [
    { icon: <Home size={20} />, label: 'Dashboard' },
    { icon: <Book size={20} />, label: 'FirstGuru' },
    { icon: <Users size={20} />, label: 'TownHall' },
    { icon: <Zap size={20} />, label: 'AI Evaluation' },
    { icon: <BarChart2 size={20} />, label: 'Performance' },
    { icon: <PenTool size={20} />, label: 'Mock Test' },
  ];

  return (
    <nav className="bg-secondary px-6 py-4">
      <div className="max-w-7xl mx-auto flex items-center justify-between">
        <div className="flex items-center space-x-8">
          <img src="/api/placeholder/40/40" alt="FirstBench" className="h-8" />
          {navItems.map((item, index) => (
            <button
              key={index}
              className="flex items-center space-x-2 text-gray-300 hover:text-white transition-colors"
            >
              {item.icon}
              <span>{item.label}</span>
            </button>
          ))}
        </div>
        <div className="flex items-center space-x-4">
          <Bell className="text-gray-300 cursor-pointer" />
          <div className="h-8 w-8 bg-gray-400 rounded-full cursor-pointer" />
        </div>
      </div>
    </nav>
  );
};

// src/components/dashboard/ResultCard.jsx
import React from 'react';
import { Card } from '../ui/Card';
import { ClipboardCheck } from 'lucide-react';

export const ResultCard = () => {
  return (
    <Card className="p-6">
      <div className="text-center mb-8">
        <h2 className="text-2xl font-bold text-primary">Your Result!</h2>
        <p className="text-gray-500 text-sm">All your insights & details in one place</p>
      </div>

      <div className="bg-gray-50 rounded-lg p-4 mb-6">
        <div className="flex justify-between items-center mb-2">
          <div className="flex items-center space-x-2">
            <div className="bg-primary/10 p-2 rounded">
              <ClipboardCheck className="text-primary" size={20} />
            </div>
            <span className="text-green-500 text-sm font-medium">YOU'VE PASSED!</span>
          </div>
          <span className="text-teal-500 text-sm">76% ACCURACY</span>
        </div>
        <div className="text-3xl font-bold">
          136<span className="text-gray-400 text-xl">/240</span>
        </div>
      </div>

      <div className="border-t pt-4">
        <h3 className="font-semibold mb-4">Top Score</h3>
        <div className="flex items-center justify-between">
          <div className="flex items-center space-x-3">
            <div className="w-10 h-10 bg-gray-200 rounded-full" />
            <div>
              <p className="text-sm text-gray-600">By Parth Akotkar</p>
              <p className="font-bold">230/240</p>
            </div>
          </div>
          <span className="text-teal-500 text-sm">92% ACCURACY</span>
        </div>
      </div>

      <button className="w-full bg-primary text-white rounded-lg py-3 mt-6 hover:bg-primary/90 transition-colors">
        Practice more
      </button>
    </Card>
  );
};
