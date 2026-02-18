<template>
    <div class="w-full min-h-screen flex justify-center items-center bg-gradient-to-br to-indigo-100">  
    <div class="w-[92%] max-w-[1400px] h-[600px] flex rounded-[20px] overflow-hidden shadow-lg border border-gray-200 bg-white">
        <div class="w-1/2 h-full relative">
            <img src="/images/peopleCore-soution.png" alt="PeopleCore Solution" class="w-full h-full object-cover">
            <div class="absolute inset-0 bg-gradient-to-tr from-blue-700/40 to-indigo-600/30"></div>
        </div>

        <!-- RIGHT FORM -->
        <form class="w-1/2 p-12 flex flex-col justify-center">

            <h3 class="text-4xl font-bold mb-3 text-center 
                       bg-gradient-to-r from-blue-600 to-indigo-600 
                       bg-clip-text text-transparent">
                How may we help you!
            </h3>

            <p class="text-center text-gray-500 mb-10">
                We'd love to hear from you. Send us a message.
            </p>

            <!-- Row 1 -->
            <div class="flex gap-6 mb-6">
                <input 
                    class="w-full p-4 bg-gray-50 border border-gray-200 rounded-xl hover:border-blue-200 hover:bg-white hover:shadow-md focus:outline-none focus:ring-1 focus:ring-blue-200  focus:border-blue-200 transition duration-300"
                    type="text"
                    placeholder="Full Name"
                    required
                />

                <input 
                    class="w-full p-4 bg-gray-50 border border-gray-200 rounded-xl hover:border-blue-200 hover:bg-white hover:shadow-md focus:outline-none focus:ring-1 focus:ring-blue-200  focus:border-blue-200 transition duration-300"
                    type="email"
                    placeholder="Email Address"
                    required
                />
            </div>

            <!-- Row 2 -->
            <div class="flex gap-6 mb-6">
                <input 
                    class="w-full p-4 bg-gray-50 border border-gray-200 rounded-xl hover:border-blue-200 hover:bg-white hover:shadow-md focus:outline-none focus:ring-1 focus:ring-blue-200  focus:border-blue-200 transition duration-300"
                    type="text"
                    placeholder="Phone Number"
                    required
                />

                <select 
                    class="w-full p-4 bg-gray-50 border border-gray-200 rounded-xl hover:border-blue-200 hover:bg-white hover:shadow-md focus:outline-none focus:ring-1 focus:ring-blue-200  focus:border-blue-200 transition duration-300"
                    required
                >
                    <option value="">Select Service</option>
                    <option>Solution</option>
                    <option>Business</option>
                    <option>Marketing</option>
                    <option>Planning</option>
                    <option>Design</option>
                </select>
            </div>

            <!-- Message -->
            <textarea class="w-full p-4 bg-gray-50 border border-gray-200 rounded-xl h-36 hover:border-blue-200 hover:bg-white hover:shadow-md focus:outline-none focus:ring-1 focus:ring-blue-200 focus:border-blue-200 transition duration-300 mb-8" 
                placeholder="Tell us about your project..." required
            ></textarea>

            <!-- Button -->
            <button 
                class="w-full py-4 rounded-xl font-semibold text-lg bg-gradient-to-r from-blue-600 to-indigo-600 hover:from-indigo-600 hover:to-blue-600 text-white shadow-lg hover:shadow-xl transition duration-300 transform hover:-translate-y-1">
                Send Message
            </button>

        </form>

    </div> 
    </div>


    <div class="w-full flex justify-center items-center bg-gradient-to-br to-indigo-50">
        <div class="w-[92%] max-w-[1400px] h-[400px] rounded-[20px] overflow-hidden shadow-sm border border-gray-200 bg-white">
            <div class="flex flex-col items-center justify-center gap-4 m-auto">
                        <h3 class="text-3xl font-bold mb-3 text-center bg-gradient-to-r from-blue-600 to-indigo-600 bg-clip-text text-transparent mt-10">
                            
                            
                        Social Media Contact
                    </h3>
                        <p class="text-center text-gray-500 mb-10">
                        We'd love to hear from you. Send us a message.
                    </p>
                        
            </div>
            <div class="flex items-center m-auto justify-center gap-8">
                    
                <!-- Facebook -->
                <a href="#"
                class="group w-40 h-40 bg-gray-50 rounded-2xl flex flex-col items-center justify-center shadow-md hover:shadow-xl hover:-translate-y-2 transition-all duration-300">

                <div class="w-14 h-14 flex items-center justify-center rounded-full bg-blue-100 group-hover:bg-blue-600 transition-all duration-300">

                    <i class="fab fa-facebook-f text-blue-600 group-hover:text-white text-xl"></i>
                </div>

                <span class="mt-4 font-semibold text-gray-800">Chork Bora</span>
                </a>

                <!-- Instagram -->
                <a href="#"
                class="group w-40 h-40 bg-gray-50 rounded-2xl flex flex-col items-center justify-center shadow-md hover:shadow-xl hover:-translate-y-2 transition-all duration-300">

                <div class="w-14 h-14 flex items-center justify-center rounded-full bg-blue-100 group-hover:bg-blue-600 transition-all duration-300">

                    <i class="fab fa-instagram text-blue-600 group-hover:text-white text-xl"></i>
                </div>

                <span class="mt-4 font-semibold text-gray-800">Chork Bora</span>
                </a>

                <!-- NUmber phone -->
                <a href="#"
                class="group w-40 h-40 bg-gray-50 rounded-2xl flex flex-col items-center justify-center shadow-md hover:shadow-xl hover:-translate-y-2 transition-all duration-300">

                <div class="w-14 h-14 flex items-center justify-center rounded-full bg-blue-100 group-hover:bg-blue-700 transition-all duration-300">

                    <i class="fa-solid fa-phone text-blue-700 group-hover:text-white text-xl"></i>
                </div>

                <span class="mt-4 font-semibold text-gray-800">0976543401</span>
                </a>
                <!-- gmail -->
                <a href="#" class="group w-40 h-40 bg-gray-50 rounded-2xl flex flex-col items-center justify-center shadow-md hover:shadow-xl hover:-translate-y-2 transition-all duration-300">

                <div class="w-14 h-14 flex items-center justify-center rounded-full bg-blue-100 group-hover:bg-blue-700 transition-all duration-300">

                    <i class="fa-solid fa-envelope text-blue-700 group-hover:text-white text-xl"></i>
                    
                </div>

                <span class="mt-4 font-semibold text-gray-800">bora4@gmail.com</span>
                </a>


                <a href="#"
                class="group w-40 h-40 bg-gray-50 rounded-2xl flex flex-col items-center justify-center shadow-md hover:shadow-xl hover:-translate-y-2 transition-all duration-300">

                <div class="w-14 h-14 flex items-center justify-center 
                            rounded-full bg-blue-100 group-hover:bg-blue-700 
                            transition-all duration-300">

                    <i class="fa-brands fa-telegram text-blue-700 group-hover:text-white text-xl"></i>
                </div>

                <span class="mt-4 font-semibold text-gray-800">Chork Bora</span>
                </a>
            </div>

        </div>      
    </div>


    <div class="w-full min-h-screen flex justify-center items-center bg-gradient-to-br to-indigo-100">
        <div class="w-[92%] max-w-[1400px] h-[600px] flex rounded-[20px] overflow-hidden shadow-lg border border-gray-200 bg-white">
            <iframe
            class="w-full h-full"
             src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3909.1012132498377!2d104.88399937464044!3d11.544596844556093!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x310950549f27fc1b%3A0x65c2d5b055de0d9d!2z4Z6i4Z6E4Z-S4Z6C4Z6A4Z624Z6a4oCL4Z6K4Z6-4Z6Y4Z-S4Z6U4Z644oCL4Z6X4Z624Z6W4Z6J4Z6J4Z654Z6Y4oCL4Z6T4Z-D4Z6A4Z674Z6Y4Z624Z6a!5e0!3m2!1skm!2skh!4v1771397836332!5m2!1skm!2skh"
            frameborder="0"
            scrolling="no"
            marginheight="0"
            marginwidth="0">
            </iframe>
        </div>
</div>
</template>