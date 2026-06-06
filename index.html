import { API_KEY } from './config.js';

document.addEventListener("DOMContentLoaded", () => {
    const chatForm = document.getElementById("chatForm");
    const userInput = document.getElementById("userInput");
    const imageInput = document.getElementById("imageInput");
    const messagesContainer = document.getElementById("messagesContainer");
    
    const newChatBtn = document.getElementById("newChatBtn");
    const chatListContainer = document.getElementById("chatListContainer");

    // const API_KEY = "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";
    

    let userName = localStorage.getItem("userName") || null;
    let selectedImageBase64 = null;
    let selectedImageMimeType = null;

    let aktivniChatIdZaEdit = null;

    let chats = JSON.parse(localStorage.getItem("zox_chats")) || {};
    let currentChatId = localStorage.getItem("zox_current_chat_id") || null;

    const formatujIme = (ime) => {
        if (!ime) return "";
        return ime.toLowerCase() === "bogdan" ? "Bogdane" : ime;
    };

    initChats();

    
    function initChats() {
        if (Object.keys(chats).length === 0) {
            createNewChat("Glavni razgovor");
        } else if (!currentChatId || !chats[currentChatId]) {
            currentChatId = Object.keys(chats)[0];
            localStorage.setItem("zox_current_chat_id", currentChatId);
        }
        
        renderChatList();
        loadChatMessages(currentChatId);
    }


    function zatvoriMeni() {
    const sidebarElement = document.querySelector(".sidebar");
    const chatContainer = document.querySelector(".chat-container");
    
    // Uklanjamo klase koje pomeraju layout
    if (sidebarElement) sidebarElement.classList.remove("open");
    if (chatContainer) chatContainer.classList.remove("sidebar-open");
}

    function createNewChat(title = "Novi razgovor") {
        const chatId = "chat_" + Date.now();
        chats[chatId] = {
            id: chatId,
            title: title,
            messages: []
        };

        zatvoriMeni();
        
        const uvodniTekst = userName 
            ? `Pozdrav, <strong>${formatujIme(userName)}</strong>. Šta radimo danas? Tu sam za kod, jednačine, sastave ili bleju.`
            : "Ćao! Ja sam tvoj asistent Zox. Kako se zoveš da bismo mogli lakše da radimo?";
        
        chats[chatId].messages.push({
            text: uvodniTekst,
            sender: "bot",
            imageSrc: null
        });

        currentChatId = chatId;
        saveChatsToLocalStorage();
        renderChatList();
        loadChatMessages(currentChatId);
    }

    function saveChatsToLocalStorage() {
        localStorage.setItem("zox_chats", JSON.stringify(chats));
        localStorage.setItem("zox_current_chat_id", currentChatId);
    }

    function renderChatList() {
        if (!chatListContainer) return;
        
        let listHtml = `<p class="history-title">Nedavno</p>`;

        Object.values(chats).reverse().forEach(chat => {
            const activeClass = chat.id === currentChatId ? "active" : "";
            listHtml += `
                <div class="history-item ${activeClass}">
                    <div class="history-item-left" data-id="${chat.id}">
                        <i class="fa-regular fa-message"></i>
                        <span class="chat-title">${chat.title}</span>
                    </div>
                    <div class="history-item-actions">
                        <button class="action-btn edit-chat" data-id="${chat.id}" title="Promeni ime">
                            <i class="fa-solid fa-pen"></i>
                        </button>
                        <button class="action-btn delete-chat" data-id="${chat.id}" title="Obriši čet">
                            <i class="fa-solid fa-trash"></i>
                        </button>
                    </div>
                </div>
            `;
        });

        chatListContainer.innerHTML = listHtml;

        const dynamicNewChatBtn = document.getElementById("newChatBtn");
        if (dynamicNewChatBtn) {
            dynamicNewChatBtn.onclick = () => {
                createNewChat();
                if (window.innerWidth <= 768) {
                    document.querySelector(".sidebar").classList.remove("open");
                }
            };
        }
    }

    // document.addEventListener("click", (e) => {
    //     const chatTarget = e.target.closest(".history-item-left");
    //     if (chatTarget) {
    //         const id = chatTarget.getAttribute("data-id");
    //         currentChatId = id;
    //         saveChatsToLocalStorage();
    //         renderChatList();
    //         loadChatMessages(currentChatId);
            
    //         if (window.innerWidth <= 768) {
    //             document.querySelector(".sidebar").classList.remove("open");
    //         }
    //         return;
    //     }

    //     const editTarget = e.target.closest(".edit-chat");
    //     if (editTarget) {
    //         e.preventDefault();
    //         const id = editTarget.getAttribute("data-id");
    //         aktivniChatIdZaEdit = id;
            
    //         const modal = document.getElementById("editModal");
    //         const modalInput = document.getElementById("modalInput");
            
    //         if (modal && modalInput) {
    //             modalInput.value = chats[id].title;
    //             modal.style.display = "flex";
    //             modalInput.focus();
    //         }
    //         return;
    //     }

    //     const deleteTarget = e.target.closest(".delete-chat");
    //     if (deleteTarget) {
    //         e.preventDefault();
    //         const id = deleteTarget.getAttribute("data-id");
            
    //         if (confirm(`Da li sigurno želiš da obrišeš razgovor "${chats[id].title}"?`)) {
    //             delete chats[id];
                
    //             if (currentChatId === id) {
    //                 const preostaliIds = Object.keys(chats);
    //                 if (preostaliIds.length > 0) {
    //                     currentChatId = preostaliIds[preostaliIds.length - 1];
    //                 } else {
    //                     createNewChat("Glavni razgovor");
    //                     return;
    //                 }
    //             }
                
    //             saveChatsToLocalStorage();
    //             renderChatList();
    //             loadChatMessages(currentChatId);
    //         }
    //         return;
    //     }
    // });



    document.addEventListener("click", (e) => {
        // --- KLIK NA ISTORIJU ---
        const chatTarget = e.target.closest(".history-item-left");
        if (chatTarget) {
            const id = chatTarget.getAttribute("data-id");
            currentChatId = id;
            saveChatsToLocalStorage();
            renderChatList();
            loadChatMessages(currentChatId);
            
            // OVO JE KLJUČNO: Zatvaramo meni čim klikneš na čet
            if (window.innerWidth <= 768) {
                closeSidebar();
            }
            return;
        }

        // --- KLIK NA EDIT ---
        const editTarget = e.target.closest(".edit-chat");
        if (editTarget) {
            e.preventDefault();
            const id = editTarget.getAttribute("data-id");
            aktivniChatIdZaEdit = id;
            const modal = document.getElementById("editModal");
            const modalInput = document.getElementById("modalInput");
            if (modal && modalInput) {
                modalInput.value = chats[id].title;
                modal.style.display = "flex";
                modalInput.focus();
            }
            return;
        }

        // --- KLIK NA DELETE ---
        const deleteTarget = e.target.closest(".delete-chat");
        if (deleteTarget) {
            e.preventDefault();
            const id = deleteTarget.getAttribute("data-id");
            if (confirm(`Da li sigurno želiš da obrišeš razgovor "${chats[id].title}"?`)) {
                delete chats[id];
                if (currentChatId === id) {
                    const preostaliIds = Object.keys(chats);
                    if (preostaliIds.length > 0) {
                        currentChatId = preostaliIds[preostaliIds.length - 1];
                    } else {
                        createNewChat("Glavni razgovor");
                        return;
                    }
                }
                saveChatsToLocalStorage();
                renderChatList();
                loadChatMessages(currentChatId);
            }
            return;
        }
    });

    const modal = document.getElementById("editModal");
    const modalInput = document.getElementById("modalInput");
    const modalSaveBtn = document.getElementById("modalSaveBtn");
    const modalCancelBtn = document.getElementById("modalCancelBtn");

    if (modalSaveBtn && modal) {
        modalSaveBtn.onclick = () => {
            const novoIme = modalInput.value.trim();
            if (novoIme !== "" && aktivniChatIdZaEdit) {
                chats[aktivniChatIdZaEdit].title = novoIme;
                saveChatsToLocalStorage();
                renderChatList();
            }
            modal.style.display = "none";
            aktivniChatIdZaEdit = null;
        };
    }

    if (modalCancelBtn && modal) {
        modalCancelBtn.onclick = () => {
            modal.style.display = "none";
            aktivniChatIdZaEdit = null;
        };
    }

    if (modal) {
        modal.onclick = (e) => {
            if (e.target === modal) {
                modal.style.display = "none";
                aktivniChatIdZaEdit = null;
            }
        };
    }

    function loadChatMessages(chatId) {
        messagesContainer.innerHTML = "";
        const currentChat = chats[chatId];
        if (!currentChat) return;

        currentChat.messages.forEach(msg => {
            appendMessageToDOM(msg.text, msg.sender, msg.imageSrc);
        });
        
        if (window.MathJax && window.MathJax.typesetPromise) {
            window.MathJax.typesetPromise();
        }
    }

    function saveMessageToHistory(text, sender, imageSrc = null) {
        if (chats[currentChatId]) {
            if (chats[currentChatId].title === "Novi razgovor" && sender === "user" && text) {
                chats[currentChatId].title = text.substring(0, 18) + (text.length > 18 ? "..." : "");
            }

            chats[currentChatId].messages.push({ text, sender, imageSrc });
            saveChatsToLocalStorage();
            if (sender === "user") renderChatList();
        }
    }

    imageInput.addEventListener("change", (e) => {
        const file = e.target.files[0];
        if (!file) return;

        selectedImageMimeType = file.type;

        const reader = new FileReader();
        reader.onload = function (event) {
            selectedImageBase64 = event.target.result.split(',')[1];
            userInput.placeholder = `Zakačen zadatak: ${file.name} (Unesi komentar/pitanje)`;
            userInput.focus();
        };
        reader.readAsDataURL(file);
    });

    chatForm.addEventListener("submit", async (e) => {
        e.preventDefault();
        const messageText = userInput.value.trim();

        if (!messageText && !selectedImageBase64) return;

        const userImgSrc = selectedImageBase64 ? `data:${selectedImageMimeType};base64,${selectedImageBase64}` : null;
        
        appendMessageToDOM(messageText, "user", userImgSrc);
        saveMessageToHistory(messageText, "user", userImgSrc);

        userInput.value = "";
        userInput.placeholder = "Unesite poruku ili zakačite sliku...";

        if (!userName) {
            handleNameSetup(messageText);
            return;
        }

        const textLower = messageText.toLowerCase();
        if (textLower.includes("zaboravi me") || textLower.includes("promeni ime")) {
            localStorage.removeItem("userName");
            userName = null;
            appendMessageDOMAndHistory("U redu, zaboravio sam tvoje ime. Kako se sada zoveš?", "bot");
            return;
        }

        const imgToSend = selectedImageBase64;
        const mimeToSend = selectedImageMimeType;

        selectedImageBase64 = null;
        selectedImageMimeType = null;
        imageInput.value = "";

        await fetchGroqResponse(messageText, imgToSend, mimeToSend);
    });

    function handleNameSetup(text) {
        let extractedName = text;
        const textLower = text.toLowerCase();

        if (textLower.includes("zovem se")) {
            extractedName = text.split(/zovem se/i)[1].trim();
        } else if (textLower.includes("ja sam")) {
            extractedName = text.split(/ja sam/i)[1].trim();
        }

        userName = extractedName.replace(/[.!]/g, "");
        localStorage.setItem("userName", userName);

        appendMessageDOMAndHistory(`Drago mi je, <strong>${userName}</strong>! Spreman sam za nauku i inženjering. Daj mi zadatak!`, "bot");
    }

async function fetchGroqResponse(userText, base64Image = null, mimeType = null) {
        const loadingMessage = appendMessageToDOM(`<div class="typing-indicator"><span></span><span></span><span></span></div>`, "bot");

        const trenutanDatumIVreme = new Date().toLocaleString("sr-RS", { 
            timeZone: "Europe/Belgrade",
            dateStyle: "full", 
            timeStyle: "medium" 
        });

        const url = "https://api.groq.com/openai/v1/chat/completions";
        
        const history = chats[currentChatId].messages.map(msg => ({
            role: msg.sender === "user" ? "user" : "assistant",
            content: msg.text
        }));

        const modelName = base64Image ? "meta-llama/llama-4-scout-17b-16e-instruct" : "llama-3.1-8b-instant";

        const requestBody = {
            model: modelName,
            messages: [
                { 
                    role: "system", 
                    content: `Ti si Zox, pomoćnik koji priča srpski. TRENUTNO VREME I DATUM: ${trenutanDatumIVreme}. Uvek budi svestan ovog vremena kada odgovaraš. Pomažeš oko nauke i koda. Pamtiš sve što smo pričali. Piši formule u LaTeX formatu ($formula$ ili $$formula$$).` 
                },
                ...history
            ],
            temperature: 0.7
        };

        if (base64Image && mimeType) {
            requestBody.messages[requestBody.messages.length - 1] = {
                role: "user",
                content: [
                    { type: "text", text: userText || "Analiziraj sliku." },
                    { type: "image_url", image_url: { url: `data:${mimeType};base64,${base64Image}` } }
                ]
            };
        }

        try {
            const response = await fetch(url, {
                method: "POST",
                headers: { "Content-Type": "application/json", "Authorization": `Bearer ${API_KEY}` },
                body: JSON.stringify(requestBody)
            });

            const data = await response.json();
            loadingMessage.remove();

            if (data.error) {
                appendMessageDOMAndHistory(`Greška: ${data.error.message}`, "bot");
                return;
            }

            appendMessageDOMAndHistory(data.choices[0].message.content, "bot");
            if (window.MathJax) window.MathJax.typesetPromise();
        } catch (error) {
            loadingMessage.remove();
            appendMessageDOMAndHistory("Greška u komunikaciji.", "bot");
        }
    }

   

    function appendMessageDOMAndHistory(text, sender) {
        appendMessageToDOM(text, sender);
        saveMessageToHistory(text, sender);
    }

    function appendMessageToDOM(text, sender, imageSrc = null) {
        const messageDiv = document.createElement("div");
        messageDiv.classList.add("message", `${sender}-message`);

        const avatarHTML = sender === "bot"
            ? `<div class="avatar"><img src="logo.png" alt="Z" class="bot-avatar-img"></div>`
            : `<div class="avatar"><i class="fa-solid fa-user"></i></div>`;

        let imageHTML = "";
        if (imageSrc) {
            imageHTML = `<img src="${imageSrc}" style="max-width: 100%; max-height: 250px; border-radius: 10px; margin-bottom: 8px; display: block;">`;
        }

        let finalContent = text;
        if (text && !text.includes("typing-indicator")) {
            finalContent = text.replace(/\n/g, '<br>');
        }

        messageDiv.innerHTML = `
            ${avatarHTML}
            <div class="text">
                ${imageHTML}
                ${finalContent ? finalContent : ""}
            </div>
        `;

        messagesContainer.appendChild(messageDiv);
        messagesContainer.scrollTop = messagesContainer.scrollHeight;

        return messageDiv;
    }

const logoBtn = document.querySelector(".logo");
const sidebarElement = document.querySelector(".sidebar");
const chatContainer = document.querySelector(".chat-container"); // Dodaj ovo

if (logoBtn && sidebarElement) {
    logoBtn.addEventListener("click", (e) => {
        if (window.innerWidth <= 768) {
            e.stopPropagation();
            sidebarElement.classList.toggle("open");
            chatContainer.classList.toggle("sidebar-open"); // Ovo pokreće animaciju
        }
    });
}


function closeSidebar() {
    const chatContainer = document.querySelector(".chat-container");
    const mainChat = document.querySelector(".chat-main");

    if (chatContainer) {
        chatContainer.classList.remove("sidebar-open");
    }
    
    // DIREKTAN RESET: Ako klasa nije vratila element, uradi ovo:
    if (mainChat) {
        mainChat.style.transform = "translateX(0)";
    }
}

});


