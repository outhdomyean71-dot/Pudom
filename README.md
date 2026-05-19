"use client";
import React from "react";

export default function Dashboard() {
  return (
    <div className="flex h-screen bg-slate-50 font-sans">
      {/* Sidebar (របារម៉ឺនុយខាងឆ្វេង) */}
      <aside className="w-64 bg-indigo-900 text-white flex flex-col shadow-xl">
        <div className="p-6 flex items-center gap-3 border-b border-indigo-800">
          <div className="w-10 h-10 bg-white text-indigo-900 flex items-center justify-center rounded-lg font-bold text-xl">
            S
          </div>
          <div>
            <h1 className="text-lg font-bold">SchoolPro</h1>
            <p className="text-xs text-indigo-300">Exam Management</p>
          </div>
        </div>
        <nav className="flex-1 p-4 space-y-2">
          <NavItem active icon="📊" text="ទិដ្ឋភាពទូទៅ (Dashboard)" />
          <NavItem icon="👨‍🎓" text="គ្រប់គ្រងសិស្ស" />
          <NavItem icon="🏫" text="ថ្នាក់រៀន & មុខវិជ្ជា" />
          <NavItem icon="📝" text="ការប្រឡង & ពិន្ទុ" />
          <NavItem icon="🏆" text="ចំណាត់ថ្នាក់ & របាយការណ៍" />
        </nav>
        <div className="p-4 border-t border-indigo-800">
          <NavItem icon="⚙️" text="ការកំណត់ (Settings)" />
        </div>
      </aside>

      {/* Main Content (ផ្ទៃបង្ហាញខាងស្តាំ) */}
      <main className="flex-1 flex flex-col overflow-hidden">
        {/* Top Header */}
        <header className="h-16 bg-white border-b border-gray-200 flex items-center justify-between px-8 shadow-sm">
          <h2 className="text-xl font-semibold text-gray-800">សួស្តី, លោកគ្រូនាយក 👋</h2>
          <div className="flex items-center gap-4">
            <button className="text-gray-500 hover:text-indigo-600 transition">🔔 ដំណឹង</button>
            <div className="w-9 h-9 bg-indigo-100 rounded-full border-2 border-indigo-500 flex items-center justify-center text-indigo-700 font-bold">
              A
            </div>
          </div>
        </header>

        {/* Dashboard Content */}
        <div className="flex-1 overflow-y-auto p-8">
          
          {/* Stat Cards (កាតស្ថិតិ) */}
          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
            <StatCard title="សិស្សសរុប (ទី១-ទី១២)" value="១,២៥០" icon="👨‍🎓" color="bg-blue-500" />
            <StatCard title="ថ្នាក់រៀនសរុប" value="៣៦" icon="🏫" color="bg-purple-500" />
            <StatCard title="គ្រូបង្រៀន" value="៤៥" icon="👨‍🏫" color="bg-orange-500" />
            <StatCard title="ការប្រឡងកំពុងបើក" value="២" icon="📝" color="bg-green-500" />
          </div>

          <div className="grid grid-cols-1 lg:grid-cols-3 gap-8">
            {/* ផ្នែកក្រាហ្វិក (កន្លែងទំនេរសម្រាប់ដាក់ Chart) */}
            <div className="lg:col-span-2 bg-white rounded-xl shadow-sm border border-gray-100 p-6">
              <h3 className="text-lg font-bold text-gray-800 mb-4">ស្ថិតិប្រឡងប្រចាំខែ</h3>
              <div className="h-64 bg-slate-50 rounded-lg flex items-center justify-center border border-dashed border-gray-300">
                <span className="text-gray-400">📊 ក្រាហ្វិកនឹងបង្ហាញនៅទីនេះ (អាចប្រើ Recharts)</span>
              </div>
            </div>

            {/* បញ្ជីសិស្សពូកែប្រចាំខែ (Top Students) */}
            <div className="bg-white rounded-xl shadow-sm border border-gray-100 p-6">
              <h3 className="text-lg font-bold text-gray-800 mb-4">សិស្សពូកែប្រចាំខែតុលា 🏆</h3>
              <div className="space-y-4">
                <TopStudent rank={1} name="សុខ សាន្ត" grade="១២A" score="៩៨.៥" />
                <TopStudent rank={2} name="ចាន់ មករា" grade="១១B" score="៩៥.០" />
                <TopStudent rank={3} name="ម៉ែន ស្រីលីន" grade="១០C" score="៩៣.២" />
                <TopStudent rank={4} name="កែវ វិច្ឆិកា" grade="១២A" score="៩១.៨" />
              </div>
              <button className="w-full mt-6 py-2 text-indigo-600 bg-indigo-50 hover:bg-indigo-100 rounded-lg font-medium transition">
                មើលចំណាត់ថ្នាក់ទាំងអស់ ➡️
              </button>
            </div>
          </div>

        </div>
      </main>
    </div>
  );
}

// === Components តូចៗជំនួយការរចនា ===

function NavItem({ icon, text, active = false }: { icon: string; text: string; active?: boolean }) {
  return (
    <a href="#" className={`flex items-center gap-3 px-4 py-3 rounded-lg transition-colors ${active ? "bg-indigo-600 text-white shadow-md" : "text-indigo-100 hover:bg-indigo-800"}`}>
      <span className="text-xl">{icon}</span>
      <span className="font-medium">{text}</span>
    </a>
  );
}

function StatCard({ title, value, icon, color }: { title: string; value: string; icon: string; color: string }) {
  return (
    <div className="bg-white p-6 rounded-xl shadow-sm border border-gray-100 flex items-center gap-5 hover:shadow-md transition-shadow">
      <div className={`w-14 h-14 ${color} text-white rounded-xl flex items-center justify-center text-2xl shadow-sm`}>
        {icon}
      </div>
      <div>
        <p className="text-sm font-medium text-gray-500 mb-1">{title}</p>
        <h4 className="text-2xl font-bold text-gray-800">{value}</h4>
      </div>
    </div>
  );
}

function TopStudent({ rank, name, grade, score }: { rank: number; name: string; grade: string; score: string }) {
  const rankColors = ["bg-yellow-400", "bg-gray-300", "bg-orange-400", "bg-indigo-100 text-indigo-700"];
  const color = rank <= 3 ? rankColors[rank - 1] : rankColors[3];
  
  return (
    <div className="flex items-center justify-between p-3 hover:bg-slate-50 rounded-lg border border-transparent hover:border-gray-100 transition">
      <div className="flex items-center gap-3">
        <div className={`w-8 h-8 rounded-full flex items-center justify-center font-bold text-sm ${rank <= 3 ? "text-white" : ""} ${color}`}>
          {rank}
        </div>
        <div>
          <h5 className="font-semibold text-gray-800 text-sm">{name}</h5>
          <p className="text-xs text-gray-500">ថ្នាក់ {grade}</p>
        </div>
      </div>
      <div className="text-right">
        <span className="font-bold text-indigo-600">{score}</span>
      </div>
    </div>
  );
}
