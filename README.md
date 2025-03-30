# two-number-prediction-gamee
import React, { useState } from "react"; import { Button } from "@/components/ui/button";

export default function TwoNumberGame() { const [selectedNumber, setSelectedNumber] = useState(null); const [betStatus, setBetStatus] = useState(null); const [wallet, setWallet] = useState(1000); const [indicator, setIndicator] = useState("red");

const placeBet = (number) => { setSelectedNumber(number); const lowestBetNumber = Math.random() < 0.5 ? 1 : 2; if (number === lowestBetNumber) { setBetStatus("Win!"); setWallet(wallet + 200); setIndicator("green"); } else { setBetStatus("Lost!"); setWallet(wallet - 100); setIndicator("red"); } };

return ( <div className="min-h-screen bg-black text-white flex flex-col items-center justify-center gap-6"> <h1 className="text-2xl font-bold">Two Number Prediction Game</h1> <div className={w-24 h-24 flex items-center justify-center rounded-full text-xl font-bold ${indicator === "red" ? "bg-red-500" : "bg-green-500"}}>{indicator.toUpperCase()}</div> <div className="flex gap-4"> <Button className="bg-red-500 text-white" onClick={() => placeBet(1)}>1</Button> <Button className="bg-green-500 text-white" onClick={() => placeBet(2)}>2</Button> </div> <p className="text-lg">{betStatus && Result: ${betStatus}}</p> <p className="text-lg">Wallet: ₹{wallet}</p> <div className="mt-4 flex gap-4"> <Button className="bg-blue-500 text-white">Deposit</Button> <Button className="bg-yellow-500 text-black">Withdraw</Button> </div> <p className="text-sm text-gray-400 mt-4">(UPI Integration Coming Soon)</p> </div> ); }
