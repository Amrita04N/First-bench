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
import React from 'react';
import {
  BarChart2, Clock, ArrowUp, Share2, Info,
  LineChart, LayoutGrid, Activity
} from 'lucide-react';
import {
  BarChart,
  Bar,
  XAxis,
  YAxis,
  CartesianGrid,
  ResponsiveContainer
} from 'recharts';

const accuracyData = [
  { id: 1, value: 85 },
  { id: 2, value: 45 },
  { id: 3, value: 35 },
  { id: 4, value: 65 },
  { id: 5, value: 55 },
  { id: 6, value: 45 },
  { id: 7, value: 65 }
];

export default function TestResultsDashboard() {
  return (
    <div className="max-w-[1400px] mx-auto p-6 bg-gray-50">
      <div className="grid grid-cols-3 gap-6">
        {/* Left Column */}
        <div className="space-y-6">
          <div className="bg-white rounded-xl p-6 shadow-sm">
            {/* Header */}
            <div className="flex gap-4 mb-6">
              <img src="/api/placeholder/80/80" alt="Result" className="w-20 h-20"/>
              <div>
                <h2 className="text-indigo-600 text-2xl font-semibold">Your Result!</h2>
                <p className="text-gray-500">All your insights & details in one place</p>
              </div>
            </div>

            {/* Score Card */}
            <div className="bg-gray-50 rounded-xl p-5 mb-6">
              <div className="flex gap-4">
                <div className="bg-indigo-100 p-3 rounded-lg h-fit">
                  <Activity className="w-6 h-6 text-indigo-600" />
                </div>
                <div>
                  <div className="bg-indigo-100 text-indigo-600 text-xs rounded-full px-3 py-1 inline-block">
                    YOU'VE PASSED!
                  </div>
                  <div className="mt-1">
                    <span className="text-3xl font-bold">136</span>
                    <span className="text-gray-500">/240</span>
                  </div>
                  <div className="bg-teal-500 text-white text-xs rounded-full px-3 py-1 inline-block">
                    76% ACCURACY
                  </div>
                </div>
              </div>

              <div className="flex gap-4 mt-4 items-center">
                <img src="/api/placeholder/48/48" alt="Top scorer" className="w-12 h-12 rounded-lg"/>
                <div>
                  <div className="text-sm text-gray-500">Top Score</div>
                  <div>
                    <span className="text-2xl font-bold">230</span>
                    <span className="text-gray-500">/240</span>
                  </div>
                  <div className="flex items-center gap-2">
                    <span className="text-sm">By Parth Akotkar</span>
                    <span className="bg-teal-500 text-white text-xs px-2 py-0.5 rounded-full">
                      92% ACCURACY
                    </span>
                  </div>
                </div>
              </div>
            </div>

            {/* Practice Section */}
            <div className="mb-4">
              <h3 className="font-medium">Improve your Marks</h3>
              <p className="text-gray-500 text-sm mb-3">
                Improve your score by practicing more.
              </p>
              <button className="w-full bg-indigo-600 text-white py-3 rounded-lg hover:bg-indigo-700 transition-colors">
                Practice more
              </button>
            </div>

            {/* Revisit Paper */}
            <div className="border rounded-xl p-4">
              <h3 className="font-medium">Revisit Paper</h3>
              <p className="text-gray-500 text-sm mb-3">
                Challenge your friends by simply sharing a link to this test
              </p>
              <button className="w-full bg-indigo-600 text-white py-3 rounded-lg hover:bg-indigo-700 transition-colors flex items-center justify-center gap-2">
                <Share2 className="w-4 h-4" />
                Visit
              </button>
              <div className="flex items-center gap-2 mt-3 text-gray-400 text-xs">
                <div className="w-4 h-4 rounded-full bg-gray-100 flex items-center justify-center text-gray-500">
                  i
                </div>
                Instructions for how to upload your handwritten material is given
              </div>
            </div>
          </div>
        </div>

        {/* Middle Column */}
        <div className="space-y-6">
          {/* Improvements */}
          <div className="bg-white rounded-xl p-6 shadow-sm">
            <div className="flex items-center gap-2 mb-4">
              <LayoutGrid className="w-5 h-5" />
              <h3 className="font-medium">Improvements</h3>
            </div>
            <div className="flex flex-wrap gap-2">
              {[
                { text: 'Geography', bg: 'bg-emerald-100', text: 'text-emerald-700' },
                { text: 'Politics', bg: 'bg-yellow-100', text: 'text-yellow-700' },
                { text: 'Current Affairs', bg: 'bg-teal-100', text: 'text-teal-700' },
                { text: 'General Studies', bg: 'bg-gray-100', text: 'text-gray-600' },
                { text: 'Mathematics', bg: 'bg-teal-100', text: 'text-teal-700' },
                { text: 'Social Studies', bg: 'bg-gray-100', text: 'text-gray-600' },
                { text: 'English Literature', bg: 'bg-red-100', text: 'text-red-700' },
                { text: 'Indian History', bg: 'bg-yellow-100', text: 'text-yellow-700' },
                { text: 'Economics', bg: 'bg-teal-100', text: 'text-teal-700' }
              ].map((item, index) => (
                <span
                  key={index}
                  className={`${item.bg} ${item.text} px-3 py-1 rounded-full text-sm`}
                >
                  {item.text}
                </span>
              ))}
            </div>
          </div>

          {/* Response Time */}
          <div className="bg-white rounded-xl p-6 shadow-sm">
            <div className="flex items-center gap-2 mb-4">
              <Clock className="w-5 h-5" />
              <h3 className="font-medium">Response Time</h3>
            </div>
            <div className="flex items-baseline gap-2">
              <span className="text-5xl font-bold text-green-500">60</span>
              <span className="text-xl text-green-500">%</span>
              <span className="text-gray-500 ml-2">
                Ans took 
                <span className="text-red-500 flex items-center gap-1 inline-flex ml-1">
                  <ArrowUp className="w-4 h-4" /> 2min
                </span>
              </span>
            </div>
            <p className="text-red-500 mt-2">You are slow !</p>
          </div>

          {/* Accuracy Graph */}
          <div className="bg-white rounded-xl p-6 shadow-sm h-64">
            <div className="flex items-center gap-2 mb-4">
              <BarChart2 className="w-5 h-5" />
              <h3 className="font-medium">Compare Accuracy</h3>
            </div>
            <ResponsiveContainer width="100%" height="80%">
              <BarChart data={accuracyData}>
                <CartesianGrid strokeDasharray="3 3" vertical={false} />
                <XAxis dataKey="id" />
                <YAxis />
                <Bar dataKey="value" fill="#818cf8" radius={[4, 4, 0, 0]} />
              </BarChart>
            </ResponsiveContainer>
          </div>
        </div>

        {/* Right Column */}
        <div className="space-y-6">
          {/* Approach Data */}
          <div className="bg-white rounded-xl p-6 shadow-sm">
            <div className="flex items-center gap-2 mb-4">
              <LineChart className="w-5 h-5" />
              <h3 className="font-medium">Approach Data</h3>
            </div>
            <div className="space-y-3">
              {[
                { percent: '25%', text: 'Based on Facts' },
                { percent: '32%', text: 'Based on Analysis' },
                { percent: '19%', text: 'Based on Elimination' },
                { percent: '24%', text: 'Based on Guess' }
              ].map((item, index) => (
                <div key={index} className="flex justify-between items-center">
                  <span className="text-indigo-600 font-medium">{item.percent}</span>
                  <span className="text-gray-600">{item.text}</span>
                </div>
              ))}
            </div>
          </div>

          {/* Suggestions */}
          <div className="bg-white rounded-xl p-6 shadow-sm">
            <h3 className="font-medium mb-4">Suggestions</h3>
            <div className="grid grid-cols-3 gap-4">
              {[
                { time: '40sec', difficulty: 'Easy', color: 'text-teal-600' },
                { time: '1.5min', difficulty: 'Medium', color: 'text-yellow-600' },
                { time: '3min', difficulty: 'Hard', color: 'text-red-600' }
              ].map((item, index) => (
                <div key={index} className="text-center">
                  <div className="bg-gray-100 rounded-full px-3 py-1 text-sm mb-1">
                    {item.time}
                  </div>
                  <span className={`text-sm ${item.color}`}>{item.difficulty}</span>
                </div>
              ))}
            </div>
          </div>

          {/* Time Taken */}
          <div className="bg-white rounded-xl p-6 shadow-sm">
            <h3 className="font-medium mb-4">Time Taken</h3>
            <div className="h-24 flex items-center">
              <div className="w-full bg-gray-200 h-2 rounded-full relative">
                <div className="absolute h-4 w-4 bg-red-500 rounded-full top-1/2 -translate-y-1/2" style={{ left: '60%' }} />
                <div className="bg-green-500 h-full rounded-full" style={{ width: '60%' }} />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
}
