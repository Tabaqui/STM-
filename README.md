## Минималка для запуска embedded под rust(STM32F103C8T6):

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

## Зависимомти:

### Проекта:

cortex-m -- низкоуровневый доступ к ядру на процессорах Cortex-M, позволяет использовать асемблер(очень долго, скучно, нудно, кучаошибок). Необходимая фича: critical-section-single-core  https://crates.io/crates/cortex-m

cortex-m-rt -- запускатр программ и минимальный рантайм для их исполнения на процессорах Cortex-M.  https://crates.io/crates/cortex-m-rt

panic-halt -- т.к. в микроконтроллерах не предусмотрен вывод и минимальный рантайм, а ошибки обрабатывать надо, то предусмотрена эта штука, заворачивающая панику в никуда.  https://crates.io/crates/panic-halt

stm32f1xx-hal -- абстракция над низким уровнем, можно не городить огород из асемблера и чтений\записи в памть. Необходимый минимальный рантайм убран в фичу, для каждого семейства микроконтоллеров необходим свой: rt. Специализированные для контроллера фичи: medium, stm32f103.  https://crates.io/crates/stm32f1xx-hal

Для добавления и обновления зависимотей последней доступной версии в проект лучше использовать add и update. Пример:

```cargo add cortex-m```

### Для сборки:

Код проекта и зависимости легко могут отличаться от приведённого примера, т.к. ну потому что.
Не забудьте оформить config.toml и memory.x нужным для контроллера образом.
Установите нужный для контроллера toolchain для сборок. Могут понадобиться средства для сборки. Для данного проекта:

```rustup target add thumbv7m-none-eabi```

```yay -S arm-none-eabi-binutils```

Также для сборки и прошивки необходим probe-rs и его последователи.


## Прошивка:

```cargo clean && cargo embed```

## P.S.:

информация актуализируется, секции дополняются...