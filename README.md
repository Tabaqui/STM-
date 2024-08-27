## Минималка для запуска embedded под rust:

.cargo/config.toml -- приведены платформа для сборки, разметка памяти под платформу(memory.x)

src/main.rs -- зависмоси, макросы в файле необходмы для работы минимума. Не всегда адекватно воспринмается rust-analyzer

Cargo.toml -- приведены минимальные необходимые зависимости

Embed.toml -- приведена минимальная конфигурация для cargo embed, --release быстрее

memory.x -- разметка памяти

## Окружение:

Linux 6.10.6-arch1-1 #1 SMP PREEMPT_DYNAMIC Mon, 19 Aug 2024 17:02:39 +0000 x86_64 GNU/Linux

rustc 1.80.1 (3f5fd8dd4 2024-08-06)

rustup 1.27.1 (2024-05-07)

cargo embed 0.24.0 (git commit: 35dbf06)

## Прошивка:

```cargo clean && cargo embed```

## P.S.:

информация актуализируется, секции дополняются...