# my-self
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>kabilesh-webtopia</title>
    <meta name="description" content="Personal Portfolio Website" />
    <meta name="author" content="Kabilesh" />
    <meta property="og:image" content="/og-image.png" />
  </head>

  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>

// src/App.tsx
import { Toaster } from "@/components/ui/toaster";
import { Toaster as Sonner } from "@/components/ui/sonner";
import { TooltipProvider } from "@/components/ui/tooltip";
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Index from "./pages/Index";

const queryClient = new QueryClient();

const App = () => (
  <QueryClientProvider client={queryClient}>
    <TooltipProvider>
      <Toaster />
      <Sonner />
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Index />} />
        </Routes>
      </BrowserRouter>
    </TooltipProvider>
  </QueryClientProvider>
);

export default App;

// src/pages/Index.tsx
import { useEffect } from "react";
import { Hero } from "@/components/Hero";
import { About } from "@/components/About";
import { Skills } from "@/components/Skills";
import { Contact } from "@/components/Contact";

const Index = () => {
  useEffect(() => {
    const handleScroll = () => {
      const reveals = document.querySelectorAll(".reveal");
      reveals.forEach((reveal) => {
        const windowHeight = window.innerHeight;
        const elementTop = reveal.getBoundingClientRect().top;
        const elementVisible = 150;
        
        if (elementTop < windowHeight - elementVisible) {
          reveal.classList.add("active");
        }
      });
    };

    window.addEventListener("scroll", handleScroll);
    handleScroll(); // Initial check
    
    return () => window.removeEventListener("scroll", handleScroll);
  }, []);

  return (
    <main className="min-h-screen">
      <Hero />
      <About />
      <Skills />
      <Contact />
    </main>
  );
};

export default Index;

// src/components/Hero.tsx
import { GithubIcon, LinkedinIcon, Mail } from "lucide-react";
import { Button } from "@/components/ui/button";

export const Hero = () => {
  return (
    <section className="min-h-screen flex items-center justify-center px-4">
      <div className="text-center space-y-8 reveal">
        <h1 className="text-4xl md:text-6xl font-bold">
          Hi, I'm <span className="text-accent">Kabilesh</span>
        </h1>
        <p className="text-xl md:text-2xl text-muted-foreground max-w-2xl mx-auto">
          A passionate developer crafting beautiful digital experiences
        </p>
        <div className="flex gap-4 justify-center">
          <Button variant="outline" size="icon">
            <GithubIcon className="h-5 w-5" />
          </Button>
          <Button variant="outline" size="icon">
            <LinkedinIcon className="h-5 w-5" />
          </Button>
          <Button variant="outline" size="icon">
            <Mail className="h-5 w-5" />
          </Button>
        </div>
      </div>
    </section>
  );
};

// src/components/About.tsx
export const About = () => {
  return (
    <section className="py-20 px-4" id="about">
      <div className="max-w-4xl mx-auto reveal">
        <h2 className="text-3xl md:text-4xl font-bold mb-8">About Me</h2>
        <div className="grid md:grid-cols-2 gap-8 items-center">
          <div>
            <img
              src="https://images.unsplash.com/photo-1488590528505-98d2b5aba04b"
              alt="Profile"
              className="rounded-lg shadow-xl"
            />
          </div>
          <div className="space-y-4">
            <p className="text-lg text-muted-foreground">
              I'm a full-stack developer with a passion for creating elegant solutions to complex problems. With expertise in modern web technologies, I build applications that make a difference.
            </p>
            <p className="text-lg text-muted-foreground">
              When I'm not coding, you can find me exploring new technologies, contributing to open-source projects, or sharing knowledge with the developer community.
            </p>
          </div>
        </div>
      </div>
    </section>
  );
};

// src/components/Skills.tsx
import { Card, CardContent } from "@/components/ui/card";

const skills = [
  { name: "code Development", level: "Expert" },
  { name: "AI Development", level: "Advanced" },
  { name: "C++,PYTHON,C", level:"learning" },
]
 help = [
  Mail:kkabilesh221@Mail.com
  ]
