<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Podcast-Themen Abstimmung</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        podcast: {
                            primary: '#4F46E5',
                            secondary: '#818CF8',
                            accent: '#FBBF24',
                            dark: '#1F2937',
                            light: '#F9FAFB'
                        }
                    }
                }
            }
        }
    </script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        
        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, #f0f4f8 0%, #e2e8f0 100%);
            min-height: 100vh;
        }
        
        .topic-card {
            transition: all 0.3s ease;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
        }
        
        .topic-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }
        
        .topic-card.selected {
            border: 3px solid #4F46E5;
            background-color: #EEF2FF;
        }
        
        .submit-btn {
            background: linear-gradient(90deg, #4F46E5 0%, #7C3AED 100%);
            transition: all 0.3s ease;
        }
        
        .submit-btn:hover {
            transform: scale(1.03);
            box-shadow: 0 10px 20px rgba(79, 70, 229, 0.3);
        }
        
        .pulse {
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(79, 70, 229, 0.4); }
            70% { box-shadow: 0 0 0 10px rgba(79, 70, 229, 0); }
            100% { box-shadow: 0 0 0 0 rgba(79, 70, 229, 0); }
        }
        
        .notification {
            transform: translateX(100%);
            transition: transform 0.3s ease;
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        .gradient-bg {
            background: linear-gradient(120deg, #4F46E5 0%, #7C3AED 100%);
        }
    </style>
</head>
<body class="text-gray-800">
    <!-- Header -->
    <header class="gradient-bg text-white py-8 shadow-lg">
        <div class="container mx-auto px-4">
            <div class="flex flex-col md:flex-row justify-between items-center">
                <div class="flex items-center mb-4 md:mb-0">
                    <i class="fas fa-podcast text-3xl mr-3"></i>
                    <h1 class="text-2xl md:text-3xl font-bold">Podcast-Themen Abstimmung</h1>
                </div>
                <p class="text-center md:text-right text-indigo-100 max-w-md">
                    Wähle dein favorisiertes Thema für die nächste Folge meines Podcasts. Jeder User hat eine Stimme pro Abstimmung.
                </p>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto px-4 py-10">
        <div class="max-w-4xl mx-auto">
            <!-- Introduction -->
            <div class="bg-white rounded-xl shadow-md p-6 mb-10 border border-gray-200">
                <h2 class="text-xl font-bold text-podcast-dark mb-3">Warum wird abgestimmt?</h2>
                <p class="text-gray-600 mb-4">
                    Deine Meinung ist wichtig für die Zukunft meines Podcasts. Mit deiner Stimme hilfst du mir, 
                    Themen auszuwählen, die interessant für dich und andere Hörer sind.
                </p>
                <div class="flex items-center bg-blue-50 p-3 rounded-lg">
                    <i class="fas fa-info-circle text-podcast-primary mr-2"></i>
                    <p class="text-sm text-podcast-dark">
                        <strong>Hinweis:</strong> Jeder User kann nur einmal abstimmen. Deine Auswahl wird verschlüsselt an mich gesendet.
                    </p>
                </div>
            </div>

            <!-- Voting Section -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-10">
                <!-- Topic 1 -->
                <div class="topic-card bg-white rounded-xl p-6 cursor-pointer border-2 border-gray-200" 
                     onclick="selectTopic('topic1')">
                    <div class="flex items-start">
                        <div class="bg-purple-100 p-3 rounded-lg mr-4">
                            <i class="fas fa-lightbulb text-purple-600 text-2xl"></i>
                        </div>
                        <div>
                            <h3 class="font-bold text-lg text-podcast-dark">Technologie & Innovation</h3>
                            <p class="text-gray-600 mt-2">
                                Diskussion über die neuesten technologischen Entwicklungen und wie sie unser Leben verändern.
                            </p>
                        </div>
                    </div>
                    <div class="mt-4 flex justify-end">
                        <span class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-purple-100 text-purple-800">
                            <i class="fas fa-chart-line mr-1"></i> Trending
                        </span>
                    </div>
                </div>

                <!-- Topic 2 -->
                <div class="topic-card bg-white rounded-xl p-6 cursor-pointer border-2 border-gray-200" 
                     onclick="selectTopic('topic2')">
                    <div class="flex items-start">
                        <div class="bg-green-100 p-3 rounded-lg mr-4">
                            <i class="fas fa-heart text-green-600 text-2xl"></i>
                        </div>
                        <div>
                            <h3 class="font-bold text-lg text-podcast-dark">Gesundheit & Wohlbefinden</h3>
                            <p class="text-gray-600 mt-2">
                                Tipps für ein gesundes Leben, mentale Gesundheit und Work-Life-Balance.
                            </p>
                        </div>
                    </div>
                    <div class="mt-4 flex justify-end">
                        <span class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-green-100 text-green-800">
                            <i class="fas fa-user-friends mr-1"></i> Beliebt
                        </span>
                    </div>
                </div>

                <!-- Topic 3 -->
                <div class="topic-card bg-white rounded-xl p-6 cursor-pointer border-2 border-gray-200" 
                     onclick="selectTopic('topic3')">
                    <div class="flex items-start">
                        <div class="bg-blue-100 p-3 rounded-lg mr-4">
                            <i class="fas fa-globe-europe text-blue-600 text-2xl"></i>
                        </div>
                        <div>
                            <h3 class="font-bold text-lg text-podcast-dark">Kultur & Gesellschaft</h3>
                            <p class="text-gray-600 mt-2">
                                Gesellschaftliche Themen, Kulturereignisse und ihre Auswirkungen auf uns.
                            </p>
                        </div>
                    </div>
                    <div class="mt-4 flex justify-end">
                        <span class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-blue-100 text-blue-800">
                            <i class="fas fa-fire mr-1"></i> Neu
                        </span>
                    </div>
                </div>
            </div>

            <!-- Submit Section -->
            <div class="bg-white rounded-xl shadow-md p-6 border border-gray-200">
                <div class="flex flex-col md:flex-row items-center justify-between">
                    <div class="mb-4 md:mb-0">
                        <h3 class="font-bold text-xl text-podcast-dark">Deine Auswahl bestätigen</h3>
                        <p class="text-gray-600 mt-1">
                            Wähle eines der Themen aus und klicke auf "Abstimmen"
                        </p>
                    </div>
                    <button id="submitBtn" 
                            class="submit-btn text-white font-bold py-3 px-8 rounded-full text-lg disabled:opacity-50 disabled:cursor-not-allowed flex items-center"
                            onclick="submitVote()" disabled>
                        <i class="fas fa-vote-yea mr-2"></i> Abstimmen
                    </button>
                </div>
            </div>
        </div>
    </main>

    <!-- Notification -->
    <div id="notification" class="notification fixed bottom-5 right-5 bg-white rounded-lg shadow-xl border border-gray-200 p-4 max-w-xs">
        <div class="flex items-start">
            <div class="flex-shrink-0">
                <i class="fas fa-check-circle text-green-500 text-xl"></i>
            </div>
            <div class="ml-3">
                <h4 class="font-bold text-gray-900">Vielen Dank für deine Stimme!</h4>
                <p class="text-gray-600 mt-1 text-sm">Deine Wahl wurde erfolgreich übermittelt.</p>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="bg-gray-800 text-gray-400 py-8 mt-12">
        <div class="container mx-auto px-4 text-center">
            <p>© 2023 Podcast-Themen Abstimmung. Alle Rechte vorbehalten.</p>
            <p class="mt-2 text-sm">Deine Stimme hilft mir, bessere Inhalte zu erstellen!</p>
        </div>
    </footer>

    <script>
        let selectedTopic = null;
        const topics = {
            topic1: "Technologie & Innovation",
            topic2: "Gesundheit & Wohlbefinden",
            topic3: "Kultur & Gesellschaft"
        };

        function selectTopic(topicId) {
            // Reset all selections
            document.querySelectorAll('.topic-card').forEach(card => {
                card.classList.remove('selected', 'pulse');
            });
            
            // Select current topic
            const selectedCard = event.currentTarget;
            selectedCard.classList.add('selected', 'pulse');
            selectedTopic = topicId;
            
            // Enable submit button
            document.getElementById('submitBtn').disabled = false;
        }

        function submitVote() {
            if (!selectedTopic) {
                alert("Bitte wähle zunächst ein Thema aus!");
                return;
            }

            // Disable button to prevent multiple submissions
            const submitBtn = document.getElementById('submitBtn');
            submitBtn.disabled = true;
            submitBtn.innerHTML = '<i class="fas fa-spinner fa-spin mr-2"></i> Wird gesendet...';

            // Simulate sending vote
            setTimeout(() => {
                // Show notification
                const notification = document.getElementById('notification');
                notification.classList.add('show');
                
                // Reset after 3 seconds
                setTimeout(() => {
                    notification.classList.remove('show');
                    resetVoting();
                }, 3000);
            }, 1500);
        }

        function resetVoting() {
            // Reset selections
            document.querySelectorAll('.topic-card').forEach(card => {
                card.classList.remove('selected', 'pulse');
            });
            
            // Reset button
            const submitBtn = document.getElementById('submitBtn');
            submitBtn.disabled = true;
            submitBtn.innerHTML = '<i class="fas fa-vote-yea mr-2"></i> Abstimmen';
            
            // Reset selection
            selectedTopic = null;
        }

        // Simulate sending email
        function sendEmail(topic) {
            // In a real implementation, you would use a service like:
            // EmailJS, Formspree, or a custom backend to send the email
            console.log(`Sending email to machelaaron@gmail.com with vote: ${topic}`);
            
            // Example using EmailJS (you would need to set up an account):
            /*
            emailjs.send("YOUR_SERVICE_ID", "YOUR_TEMPLATE_ID", {
                to_email: "machelaaron@gmail.com",
                topic: topic
            });
            */
        }

        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            // Add pulse animation to first topic for visual interest
            document.querySelector('.topic-card').classList.add('pulse');
        });
    </script>
</body>
</html>
