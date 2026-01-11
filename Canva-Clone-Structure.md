canva-clone/
├── README.md
├── package.json
├── tsconfig.json
│
├── src/
│   ├── main.tsx                      # App entry point
│   │
│   ├── components/
│   │   ├── Canvas/
│   │   │   ├── Canvas.tsx           # Main canvas component
│   │   │   ├── Layer.tsx            # Layer management
│   │   │   ├── Grid.tsx             # Snap-to-grid
│   │   │   └── Ruler.tsx            # Ruler guides
│   │   │
│   │   ├── Toolbar/
│   │   │   ├── Toolbar.tsx          # Top toolbar
│   │   │   ├── ShapeTools.tsx       # Shape insertion
│   │   │   ├── TextTools.tsx        # Text formatting
│   │   │   └── ColorPicker.tsx      # Color selection
│   │   │
│   │   ├── Panels/
│   │   │   ├── LayersPanel.tsx      # Layers sidebar
│   │   │   ├── PropertiesPanel.tsx  # Element properties
│   │   │   └── TemplatesPanel.tsx   # Template library
│   │   │
│   │   └── shared/
│   │       ├── Button.tsx
│   │       ├── Input.tsx
│   │       └── Modal.tsx
│   │
│   ├── engine/
│   │   ├── CanvasEngine.ts          # Core canvas operations
│   │   ├── LayoutEngine.ts          # Auto-layout algorithms
│   │   ├── ColorHarmony.ts          # Color palette generation
│   │   ├── FontPairing.ts           # Font recommendation
│   │   └── SnapToGrid.ts            # Alignment algorithms
│   │
│   ├── ai/
│   │   ├── DesignAI.ts              # AI design suggestions
│   │   ├── LayoutDetector.ts        # Layout analysis (ONNX)
│   │   ├── ImageClassifier.ts       # MobileNet v3
│   │   └── ModelLoader.ts           # ONNX model manager
│   │
│   ├── storage/
│   │   ├── ProjectStore.ts          # IndexedDB for projects
│   │   ├── AssetStore.ts            # Image/font storage
│   │   └── TemplateStore.ts         # Template cache
│   │
│   ├── utils/
│   │   ├── export.ts                # PNG/PDF export
│   │   ├── math.ts                  # Geometry calculations
│   │   └── color.ts                 # Color conversion
│   │
│   ├── models/                       # AI models (ONNX)
│   │   ├── mobilenet_v3.onnx        # 20MB - Image classification
│   │   ├── layoutlm_small.onnx      # 200MB - Layout detection
│   │   └── clip_vit_b32.onnx        # 400MB - Image-text (desktop only)
│   │
│   └── templates/                    # Pre-built templates (JSON)
│       ├── social-media/
│       ├── presentations/
│       └── marketing/
│
├── public/
│   ├── fonts/                        # Embedded fonts
│   ├── icons/
│   └── sample-images/
│
├── desktop/                          # Electron/Tauri config
│   ├── main.ts                      # Main process
│   ├── preload.ts                   # Bridge
│   └── tauri.conf.json
│
├── mobile/                           # Capacitor config
│   ├── capacitor.config.ts
│   ├── ios/
│   └── android/
│
└── tests/
    ├── canvas.test.ts
    └── ai.test.ts
