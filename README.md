<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Podcast Theme Voting</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#6366f1',
                        secondary: '#8b5cf6',
                        accent: '#ec4899',
                        dark: '#1e293b',
                        light: '#f8fafc'
                    }
                }
            }
        }
    </script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');
        
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #0f172a, #1e293b);
            color: #f8fafc;
            min-height: 100vh;
        }
        
        .theme-card {
            transition: all 0.3s ease;
            transform: translateY(0);
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.2);
        }
        
        .theme-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.3);
        }
        
        .theme-card.active {
            transform: scale(1.05);
            box-shadow: 0 0 0 4px rgba(99, 102, 241, 0.5);
        }
        
        .pulse {
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% {
                box-shadow: 0 0 0 0 rgba(99, 102, 241, 0.7);
            }
            70% {
                box-shadow: 0 0 0 15px rgba(99, 102, 241, 0);
            }
            100% {
                box-shadow: 0 0 0 0 rgba(99, 102, 241, 0);
            }
        }
        
        .submit-btn {
            background: linear-gradient(90deg, #6366f1, #8b5cf6);
            transition: all 0.3s ease;
        }
        
        .submit-btn:hover {
            background: linear-gradient(90deg, #8b5cf6, #6366f1);
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(99, 102, 241, 0.3);
        }
        
        .theme-icon {
            font-size: 3rem;
            transition: all 0.3s ease;
        }
        
        .theme-card:hover .theme-icon {
            transform: scale(1.2);
        }
        
        .form-container {
            backdrop-filter: blur(10px);
            background: rgba(30, 41, 59, 0.7);
            border: 1px solid rgba(148, 163, 184, 0.2);
        }
        
        .thank-you {
            animation: fadeIn 1s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body class="flex flex-col min-h-screen">
    <!-- Header -->
    <header class="py-6 px-4 sm:px-8">
        <div class="container mx-auto flex justify-between items-center">
            <div class="flex items-center space-x-2">
                <i class="fas fa-podcast text-3xl text-primary"></i>
                <h1 class="text-2xl font-bold">Podcast<span class="text-primary">Choice</span></h1>
            </div>
            <nav>
                <ul class="flex space-x-6">
                    <li><a href="#" class="hover:text-primary transition">Home</a></li>
                    <li><a href="#" class="hover:text-primary transition">Episodes</a></li>
                    <li><a href="#" class="hover:text-primary transition">About</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Main Content -->
    <main class="flex-grow container mx-auto px-4 py-8">
        <div class="text-center mb-12">
            <h1 class="text-4xl md:text-5xl font-bold mb-4">Wähle das nächste Thema für meinen Podcast</h1>
            <p class="text-xl text-gray-300 max-w-2xl mx-auto">Hilf mir zu entscheiden, über welches Thema ich im nächsten Podcast sprechen soll. Wähle einfach eines der folgenden Themen aus und gib deine E-Mail-Adresse an.</p>
        </div>

        <!-- Theme Selection Section -->
        <section class="mb-16">
            <h2 class="text-2xl font-bold text-center mb-8">Was soll das nächste Thema sein?</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-6xl mx-auto">
                <!-- Theme 1 -->
                <div id="theme1" class="theme-card bg-dark rounded-2xl p-6 cursor-pointer flex flex-col" onclick="selectTheme(1)">
                    <div class="flex justify-center mb-4">
                        <i class="theme-icon fas fa-rocket text-primary"></i>
                    </div>
                    <h3 class="text-xl font-bold text-center mb-3">Künstliche Intelligenz & Zukunft</h3>
                    <p class="text-gray-300 text-center mb-4 flex-grow">Wie verändert KI unsere Gesellschaft? Welche ethischen Fragen ergeben sich?</p>
                    <div class="flex justify-center">
                        <span class="bg-primary bg-opacity-20 text-primary px-4 py-1 rounded-full text-sm">Technologie</span>
                    </div>
                </div>
                
                <!-- Theme 2 -->
                <div id="theme2" class="theme-card bg-dark rounded-2xl p-6 cursor-pointer flex flex-col" onclick="selectTheme(2)">
                    <div class="flex justify-center mb-4">
                        <i class="theme-icon fas fa-seedling text-secondary"></i>
                    </div>
                    <h3 class="text-xl font-bold text-center mb-3">Nachhaltigkeit & Klimawandel</h3>
                    <p class="text-gray-300 text-center mb-4 flex-grow">Wie können wir unseren Lebensstil anpassen, um das Klima zu schützen?</p>
                    <div class="flex justify-center">
                        <span class="bg-secondary bg-opacity-20 text-secondary px-4 py-1 rounded-full text-sm">Umwelt</span>
                    </div>
                </div>
                
                <!-- Theme 3 -->
                <div id="theme3" class="theme-card bg-dark rounded-2xl p-6 cursor-pointer flex flex-col" onclick="selectTheme(3)">
                    <div class="flex justify-center mb-4">
                        <i class="theme-icon fas fa-brain text-accent"></i>
                    </div>
                    <h3 class="text-xl font-bold text-center mb-3">Psychische Gesundheit</h3>
                    <p class="text-gray-300 text-center mb-4 flex-grow">Wie können wir unsere mentale Gesundheit verbessern und verstehen?</p>
                    <div class="flex justify-center">
                        <span class="bg-accent bg-opacity-20 text-accent px-4 py-1 rounded-full text-sm">Gesundheit</span>
                    </div>
                </div>
            </div>
            
            <div class="mt-8 text-center">
                <p class="text-gray-400">Klicke auf ein Thema, um es auszuwählen</p>
            </div>
        </section>

        <!-- Email Form Section -->
        <section class="mb-16">
            <div class="max-w-2xl mx-auto form-container rounded-2xl p-8">
                <h2 class="text-2xl font-bold text-center mb-2">Sende deine Wahl</h2>
                <p class="text-center text-gray-300 mb-8">Gib deine E-Mail-Adresse ein, um deine Wahl zu bestätigen</p>
                
                <form id="voteForm" action="https://formspree.io/f/xyzppvgy" method="POST" class="space-y-6">
                    <div>
                        <label for="email" class="block mb-2 font-medium">Deine E-Mail-Adresse</label>
                        <input 
                            type="email" 
                            id="email" 
                            name="email" 
                            required
                            class="w-full px-4 py-3 rounded-lg bg-slate-800 border border-slate-700 focus:border-primary focus:outline-none focus:ring-2 focus:ring-primary text-white"
                            placeholder="deine.email@beispiel.de">
                    </div>
                    
                    <div>
                        <label for="message" class="block mb-2 font-medium">Nachricht (optional)</label>
                        <textarea 
                            id="message" 
                            name="message" 
                            rows="3"
                            class="w-full px-4 py-3 rounded-lg bg-slate-800 border border-slate-700 focus:border-primary focus:outline-none focus:ring-2 focus:ring-primary text-white"
                            placeholder="Hast du noch etwas zum Thema hinzuzufügen?"></textarea>
                    </div>
                    
                    <input type="hidden" id="selectedTheme" name="selectedTheme" value="">
                    
                    <div class="text-center">
                        <button type="submit" class="submit-btn text-white font-bold py-3 px-8 rounded-full text-lg w-full sm:w-auto">
                            <i class="fas fa-paper-plane mr-2"></i> Jetzt senden
                        </button>
                    </div>
                </form>
                
                <div id="thankYouMessage" class="thank-you bg-green-900 bg-opacity-30 border border-green-700 rounded-lg p-6 mt-6 hidden">
                    <div class="flex items-center justify-center">
                        <i class="fas fa-check-circle text-green-400 text-2xl mr-3"></i>
                        <h3 class="text-xl font-bold">Vielen Dank für deine Teilnahme!</h3>
                    </div>
                    <p class="text-center mt-2">Deine Wahl wurde erfolgreich übermittelt. Ich melde mich bald bei dir!</p>
                </div>
            </div>
        </section>

        <!-- Results Section -->
        <section class="text-center">
            <h2 class="text-2xl font-bold mb-4">Aktuelle Ergebnisse</h2>
            <div class="max-w-3xl mx-auto bg-dark bg-opacity-50 rounded-2xl p-6">
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    <div class="bg-slate-800 rounded-xl p-4">
                        <div class="text-primary text-2xl font-bold mb-2">42%</div>
                        <div class="flex items-center justify-center mb-2">
                            <i class="fas fa-rocket mr-2"></i>
                            <span>KI & Zukunft</span>
                        </div>
                        <div class="w-full bg-gray-700 rounded-full h-2.5">
                            <div class="bg-primary h-2.5 rounded-full" style="width: 42%"></div>
                        </div>
                    </div>
                    <div class="bg-slate-800 rounded-xl p-4">
                        <div class="text-secondary text-2xl font-bold mb-2">35%</div>
                        <div class="flex items-center justify-center mb-2">
                            <i class="fas fa-seedling mr-2"></i>
                            <span>Nachhaltigkeit</span>
                        </div>
                        <div class="w-full bg-gray-700 rounded-full h-2.5">
                            <div class="bg-secondary h-2.5 rounded-full" style="width: 35%"></div>
                        </div>
                    </div>
                    <div class="bg-slate-800 rounded-xl p-4">
                        <div class="text-accent text-2xl font-bold mb-2">23%</div>
                        <div class="flex items-center justify-center mb-2">
                            <i class="fas fa-brain mr-2"></i>
                            <span>Psychische Gesundheit</span>
                        </div>
                        <div class="w-full bg-gray-700 rounded-full h-2.5">
                            <div class="bg-accent h-2.5 rounded-full" style="width: 23%"></div>
                        </div>
                    </div>
                </div>
                <p class="mt-4 text-gray-400 text-sm">Letztes Update: Gestern, 14:32 Uhr</p>
            </div>
        </section>
    </main>
<div class="mt-8 flex justify-center">
  <a href="https://docs.google.com/forms/d/e/1FAIpQLSe96idCVyKU9XoRtDbVuUxnK7MLJkJ03ozaSBM_Jmj5w5oerQ/viewform?usp=dialog" target="_blank" 
     class="bg-gradient-to-r from-purple-600 to-blue-600 text-white px-6 py-3 rounded-full shadow-lg hover:scale-105 transform transition-all duration-300">
    📬 Feedback / Kontaktformular öffnen
  </a>
</div>
    <!-- Footer -->
    <footer class="py-8 text-center text-gray-400 border-t border-slate-800 mt-8">
        <div class="container mx-auto">
            <p>© 2023 PodcastChoice. Alle Rechte vorbehalten.</p>
            <p class="mt-2">Erstellt für Machelaaron</p>
        </div>
    </footer>

    <script>
        let selectedThemeIndex = null;
        const themes = [
            "Künstliche Intelligenz & Zukunft",
            "Nachhaltigkeit & Klimawandel",
            "Psychische Gesundheit"
        ];
        
        function selectTheme(index) {
            // Remove active class from all cards
            document.querySelectorAll('.theme-card').forEach(card => {
                card.classList.remove('active', 'pulse');
            });
            
            // Add active class to selected card
            document.getElementById(`theme${index}`).classList.add('active', 'pulse');
            
            // Store selected theme
            selectedThemeIndex = index;
            document.getElementById('selectedTheme').value = themes[index - 1];
        }
        
        // Form submission handling
        document.getElementById('voteForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Get form data
            const email = document.getElementById('email').value;
            const message = document.getElementById('message').value;
            const theme = selectedThemeIndex ? themes[selectedThemeIndex - 1] : "Kein Thema ausgewählt";
            
            // In a real implementation, this would be sent to formspree
            // For this demo, we'll just show the thank you message
            document.getElementById('voteForm').classList.add('hidden');
            document.getElementById('thankYouMessage').classList.remove('hidden');
            
            // Log data to console for demonstration
            console.log("Form submitted with:");
            console.log("Email:", email);
            console.log("Selected Theme:", theme);
            console.log("Message:", message);
        });
        
        // Set initial focus on email field
        window.onload = function() {
            document.getElementById('email').focus();
        };
    </script>
</body>
</html>
