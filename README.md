# Scatter Chart Using Recharts and Tailwind CSS

```tsx
import React from "react"
import {
  CartesianGrid,
  Legend,
  ResponsiveContainer,
  Scatter,
  ScatterChart,
  Tooltip,
  XAxis,
  YAxis,
  ZAxis,
} from "recharts"

import { numberWithCommas } from "@/lib/helper"
import { cn } from "@/lib/utils"

const data01 = [
  {
    x: 100,
    y: 200,
    z: 200,
  },
  {
    x: 120,
    y: 100,
    z: 260,
  },
  {
    x: 170,
    y: 300,
    z: 400,
  },
  {
    x: 140,
    y: 250,
    z: 280,
  },
  {
    x: 150,
    y: 400,
    z: 500,
  },
  {
    x: 110,
    y: 280,
    z: 200,
  },
]

const data02 = [
  {
    x: 200,
    y: 260,
    z: 240,
  },
  {
    x: 240,
    y: 290,
    z: 220,
  },
  {
    x: 190,
    y: 290,
    z: 250,
  },
  {
    x: 198,
    y: 250,
    z: 210,
  },
  {
    x: 180,
    y: 280,
    z: 260,
  },
  {
    x: 210,
    y: 220,
    z: 230,
  },
]

export default function ScatterChartExample() {
  return (
    <ResponsiveContainer width="100%" height="100%">
      <ScatterChart width={500} height={300}>
        <CartesianGrid strokeDasharray="3 3" opacity={0.2} vertical={false} />
        <XAxis
          dataKey="x"
          type="number"
          name="stature"
          unit="cm"
          domain={[0, 260]}
          axisLine={false}
          tickLine={false}
          height={55}
          fontSize={14}
          stroke="#e5e5e5"
        />

        <YAxis
          dataKey="y"
          type="number"
          name="weight"
          unit="kg"
          axisLine={false}
          tickLine={false}
          tick={{ dx: -7 }}
          stroke="#e5e5e5"
          fontSize={14}
        />

        <ZAxis
          dataKey="z"
          type="number"
          range={[64, 144]}
          name="score"
          unit="km"
        />

        <Tooltip
          position={{ y: 0 }}
          wrapperStyle={{ outline: "none" }}
          cursor={{ fill: "#fafafa", opacity: "0.15" }}
          content={({ payload }) => {
            return (
              <div className="min-w-[8rem] divide-y divide-brand-200 rounded-md border border-brand-200 bg-brand-50 text-brand-700 shadow dark:divide-brand-700 dark:border-brand-700 dark:bg-brand-900 dark:text-brand-200">
                <ul className="px-4 py-1.5">
                  {payload.map((p, i) => {
                    return (
                      <li key={i} className="text-sm">
                        <svg
                          className={cn("mr-2 inline h-2 w-2")}
                          fill={
                            i === 0
                              ? "#60a5fa"
                              : i === 1
                              ? "#fbbf24"
                              : "#f59e0b"
                          }
                          viewBox="0 0 8 8"
                        >
                          <circle cx={4} cy={4} r={4} />
                        </svg>
                        {`${p.name}: `}
                        {numberWithCommas(p.value.toString())}
                      </li>
                    )
                  })}
                </ul>
              </div>
            )
          }}
        />
        <Legend
          layout="horizontal"
          verticalAlign="top"
          align="center"
          content={({ payload }) => {
            return (
              <ul className="sticky left-3 flex w-fit gap-4 pb-6 pl-1">
                {payload.map((p, i) => (
                  <li key={i}>
                    <svg
                      className={cn("mr-2 inline h-2 w-2")}
                      fill={i === 0 ? "#60a5fa" : "#fbbf24"}
                      viewBox="0 0 8 8"
                    >
                      <circle cx={4} cy={4} r={4} />
                    </svg>
                    {p.value}
                  </li>
                ))}
              </ul>
            )
          }}
        />
        <Scatter
          name="A school"
          data={data01}
          strokeWidth={2}
          stroke="#60a5fa"
          fill="#171717"
        />
        <Scatter
          name="B school"
          data={data02}
          strokeWidth={2}
          stroke="#fbbf24"
          fill="#171717"
        />
      </ScatterChart>
    </ResponsiveContainer>
  )
}
```
