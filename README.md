# Y2K-SOCIAL-SITE-
import { useState, useEffect } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { motion } from "framer-motion"; import { FaInstagram, FaTiktok, FaYoutube } from "react-icons/fa";

const socialLinks = [ { name: "Instagram", icon: FaInstagram, url: "https://instagram.com/arpduhrito" }, { name: "TikTok", icon: FaTiktok, url: "https://tiktok.com/@jeffhardysnephew" }, { name: "YouTube", icon: FaYoutube, url: "https://youtube.com/@arpduhrito" }, ];

export default function Y2KSocialLinks() { const [hovered, setHovered] = useState(null);

useEffect(() => { const audio = new Audio("/sounds/startup.mp3"); audio.volume = 0.3; audio.play(); }, []);

return ( <main className="min-h-screen bg-gradient-to-br from-[#FF4FE0] to-[#00CFFF] flex flex-col items-center justify-center p-4 text-white font-bold font-mono overflow-hidden"> <motion.h1 initial={{ opacity: 0, y: -40 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.8 }} className="text-5xl md:text-6xl mb-8 drop-shadow-lg glitch-text" > BURN THE CD 🔗 </motion.h1>

<div className="grid grid-cols-1 sm:grid-cols-2 gap-6 max-w-md w-full">
    {socialLinks.map((link, idx) => (
      <motion.div
        key={idx}
        className="bg-black/30 backdrop-blur-xl p-4 rounded-2xl shadow-xl border border-white/10 glitch-box"
        whileHover={{ scale: 1.05, rotate: -2 }}
        onMouseEnter={() => {
          setHovered(idx);
          const click = new Audio("/sounds/select.mp3");
          click.volume = 0.2;
          click.play();
        }}
        onMouseLeave={() => setHovered(null)}
      >
        <a href={link.url} target="_blank" rel="noopener noreferrer" className="flex items-center space-x-4">
          <link.icon size={28} className="text-white" />
          <span className="text-lg tracking-wider">{link.name}</span>
        </a>
      </motion.div>
    ))}
  </div>

  <motion.footer
    initial={{ opacity: 0 }}
    animate={{ opacity: 1 }}
    transition={{ delay: 1.2 }}
    className="mt-12 text-xs text-white/60"
  >
    Powered by you. Designed by Twin.
  </motion.footer>

  <style jsx>{`
    .glitch-text {
      position: relative;
      animation: glitch 1.5s infinite;
    }

    .glitch-box:hover {
      animation: boxGlitch 0.4s steps(2, end) infinite;
    }

    @keyframes glitch {
      0% { text-shadow: 2px 0 red, -2px 0 cyan; }
      20% { text-shadow: -2px 0 red, 2px 0 cyan; }
      40% { text-shadow: 2px 2px red, -2px -2px cyan; }
      60% { text-shadow: -2px -2px red, 2px 2px cyan; }
      80% { text-shadow: 2px -2px red, -2px 2px cyan; }
      100% { text-shadow: -2px 2px red, 2px -2px cyan; }
    }

    @keyframes boxGlitch {
      0%, 100% { transform: translate(0, 0); }
      33% { transform: translate(1px, -1px); }
      66% { transform: translate(-1px, 1px); }
    }
  `}</style>
</main>

); }

