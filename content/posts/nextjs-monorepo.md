---
title: "Nextjs Monorepo"
categories: ["nextjs"]
date: 2026-10-19T11:11:06+09:00
draft: false
---

## pnpm + Turborepo + Next.js (App Router) 조합으로 모노레포를 구축하는 세팅

1. 프로젝트 폴더 구조 목표
```
modoo-monorepo/
├── apps/
│   ├── modoo-tango/     # 홍보용 웹사이트 (Port 3000)
│   └── tango-talk/      # 수강생 관리 PWA 앱 (Port 3001)
├── packages/
│   ├── ui/              # 공통 UI 컴포넌트 (shadcn/ui, Tailwind)
│   ├── database/        # Supabase 클라이언트 & TypeScript 자동 생성 타입
│   └── config/          # ESLint, TypeScript 공통 설정
├── pnpm-workspace.yaml
├── turbo.json
└── package.json
```