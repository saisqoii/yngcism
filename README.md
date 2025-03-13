import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { motion } from "framer-motion";
import { FaHeart } from "react-icons/fa";

const riddles = [
  { question: "Wat is zacht, roze en smelt op je tong?", answer: "suikerspin" },
  { question: "Welke bloem symboliseert liefde en is vaak roze?", answer: "roos" },
  { question: "Wat zegt een kat als hij blij is?", answer: "miauw" },
  { question: "Welke zoete lekkernij is rond en heeft een gat in het midden?", answer: "donut" },
  { question: "Wat draag je om je outfit schattiger te maken?", answer: "strik" },
  { question: "Welke vrucht is klein, roze en zoet?", answer: "aardbei" },
  { question: "Wat gebruik je om een brief te sluiten met liefde?", answer: "zegel" },
  { question: "Wat is een magisch dier met een hoorn en roze manen?", answer: "eenhoorn" },
  { question: "Wat is zacht, knuffelbaar en gevuld met pluche?", answer: "knuffelbeer" },
  { question: "Wat geeft licht en is roze in een trendy kamer?", answer: "neonlamp" }
];

export default function CuteEscapeRoom() {
  const [step, setStep] = useState(0);
  const [input, setInput] = useState("");
  const [isCompleted, setIsCompleted] = useState(false);

  const checkAnswer = () => {
    if (input.toLowerCase() === riddles[step].answer) {
      if (step === riddles.length - 1) {
        setIsCompleted(true);
      } else {
        setStep(step + 1);
        setInput("");
      }
    }
  };

  return (
    <div className="min-h-screen flex flex-col items-center justify-center bg-pink-200 p-4 text-pink-900 font-semibold">
      <motion.div className="text-3xl font-bold mb-4" animate={{ scale: [1, 1.1, 1] }}>
        🎀 Cute Pink Escape Room 🎀
      </motion.div>
      <Card className="w-96 bg-pink-100 shadow-xl rounded-2xl border-2 border-white p-4 text-center">
        <CardContent>
          {isCompleted ? (
            <div>
              <p className="text-xl">Gefeliciteerd! 🎉 Je hebt alle raadsels opgelost!</p>
              <FaHeart className="text-pink-500 text-3xl mt-2 animate-bounce" />
            </div>
          ) : (
            <div>
              <p className="text-lg mb-2">{riddles[step].question}</p>
              <Input
                className="w-full rounded-full border-2 border-pink-400 px-4 py-2 text-center"
                value={input}
                onChange={(e) => setInput(e.target.value)}
                placeholder="Typ je antwoord..."
              />
              <Button
                className="mt-2 w-full bg-pink-500 text-white rounded-full hover:bg-pink-600"
                onClick={checkAnswer}
              >
                Antwoord
              </Button>
            </div>
          )}
        </CardContent>
      </Card>
    </div>
  );
}
