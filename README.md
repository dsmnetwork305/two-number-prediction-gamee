# two-number-prediction gamee
import React, { useState } from "react";
import { Button } from "@/components/ui/button";

export default function TwoNumberGame() {
  const [selectedNumber, setSelectedNumber] = useState(null);
  const [betStatus, setBetStatus] = useState(null);
  const [wallet, setWallet] = useState(1000);
  const [indicator, setIndicator] = useState("red");

  const placeBet = (number) => {
    setSelectedNumber(number);
    const lowestBetNumber = Math.random() < 0.5 ? 1 : 2;
    if (number === lowestBetNumber) {
      setBetStatus("Win!");
      setWallet(wallet + 200);
      setIndicator("green");
    } else {
      setBetStatus("Lost!");
      setWallet(wallet - 100);
      setIndicator("red");
    }
  };

  return (
    <div className="flex flex-col items-center gap-4 p-6">
      <h1 className="text-2xl font-bold">Two Number Prediction Game</h1>
      <div
        className={`w-24 h-24 flex items-center justify-center rounded-full text-xl font-bold ${
          indicator === "red" ? "bg-red-500" : "bg-green-500"
        }`}
      >
        {indicator.toUpperCase()}
      </div>
      <div className="flex gap-4">
        <Button className="bg-red-500 text-white px-4 py-2" onClick={() => placeBet(1)}>
          1
        </Button>
        <Button className="bg-green-500 text-white px-4 py-2" onClick={() => placeBet(2)}>
          2
        </Button>
      </div>
      {betStatus && <p className="text-lg font-semibold">Result: {betStatus}</p>}
      <p className="text-lg">Wallet: ₹{wallet}</p>
      <div className="flex gap-2">
        <Button className="bg-blue-500 text-white px-4 py-2">Deposit</Button>
        <Button className="bg-gray-500 text-white px-4 py-2">Withdraw</Button>
      </div>
      <p className="text-sm text-gray-500">(UPI Integration Coming Soon)</p>
    </div>
  );
}

