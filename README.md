# 🎨 Canva Clone - Offline Design Editor

> AI-powered design tool with template library, works 100% offline

## Features

✅ **Design Tools**
- Drag-and-drop canvas editor
- Shapes, text, images, icons
- Layers & grouping
- Snap-to-grid alignment

✅ **AI-Powered**
- Smart layout suggestions (LayoutLM)
- Auto color palette (Color Harmony algorithm)
- Font pairing recommendations
- Design quality scoring

✅ **Templates**
- 50+ pre-built templates
- Social media posts
- Presentations
- Marketing materials

✅ **Offline First**
- Works without internet
- Local storage (IndexedDB)
- Export PNG/PDF/SVG

## Tech Stack

**Frontend:** React 18 + TypeScript  
**Canvas:** Fabric.js (interactive objects)  
**AI Models:** ONNX Runtime Web  
**Storage:** IndexedDB (Dexie.js)  
**Desktop:** Tauri (Rust-based)  
**Mobile:** Capacitor  

## AI Models Used

| Model | Size | Purpose | Platform |
|-------|------|---------|----------|
| MobileNet v3 | 20MB | Image classification | All |
| LayoutLM-small | 200MB | Layout detection | All |
| CLIP-ViT-B/32 | 400MB | Image-text understanding | Desktop only |

## Installation

```bash
# Install dependencies
npm install

# Run development server
npm run dev

# Build desktop app
npm run build:desktop

# Build mobile app
npm run build:mobile
```

## Project Structure

```
src/
  components/   # React UI components
  engine/       # Canvas & layout algorithms
  ai/           # AI model integration
  storage/      # IndexedDB operations
  models/       # ONNX model files
```

## Key Algorithms

### 1. Auto-Layout Engine
Uses Flexbox-inspired constraints to automatically arrange elements.

```typescript
function autoLayout(elements: Element[]): Element[] {
  // Calculate bounding boxes
  // Apply spacing constraints (8px, 16px, 24px)
  // Align to grid (snap within 5px threshold)
  return arrangedElements;
}
```

### 2. Color Harmony
Generates complementary, analogous, and triadic color schemes.

```typescript
function generatePalette(baseColor: string): string[] {
  const hue = rgbToHsl(baseColor).h;
  return [
    hslToRgb(hue, s, l),                    // Base
    hslToRgb((hue + 180) % 360, s, l),      // Complementary
    hslToRgb((hue + 30) % 360, s, l),       // Analogous 1
    hslToRgb((hue - 30) % 360, s, l),       // Analogous 2
  ];
}
```

### 3. Snap-to-Grid
Magnetic alignment with configurable threshold.

```typescript
function snapToGrid(x: number, gridSize: number = 8, threshold: number = 5): number {
  const snapped = Math.round(x / gridSize) * gridSize;
  return Math.abs(x - snapped) < threshold ? snapped : x;
}
```

## AI Model Integration

### Loading Models

```typescript
import * as ort from 'onnxruntime-web';

const session = await ort.InferenceSession.create('/models/mobilenet_v3.onnx');
const feeds = { input: tensor };
const results = await session.run(feeds);
```

### Design Suggestions

```typescript
async function suggestLayout(elements: Element[]): Suggestion[] {
  // Run LayoutLM to detect layout issues
  // Score design quality (0-100)
  // Return actionable suggestions
}
```

## Storage Schema

### Projects Table
```typescript
interface Project {
  id: string;
  name: string;
  elements: Element[];
  createdAt: Date;
  lastModified: Date;
}
```

### Assets Table
```typescript
interface Asset {
  id: string;
  type: 'image' | 'font' | 'icon';
  data: Blob;
  metadata: {
    width?: number;
    height?: number;
  };
}
```

## Export Formats

**PNG:** Canvas.toBlob()  
**PDF:** jsPDF library  
**SVG:** Convert Fabric.js objects to SVG paths  

## Performance Optimizations

1. **Lazy Loading:** Load AI models only when needed
2. **WebWorkers:** Run inference in background thread
3. **Virtual Scrolling:** For template library
4. **Debounced Saves:** Auto-save every 5 seconds
5. **Compressed Models:** GPTQ 4-bit quantization

## Platform-Specific Features

### Desktop (Tauri)
- Native file picker
- Drag-drop files from OS
- System fonts access
- Larger model cache (2GB)

### Mobile (Capacitor)
- Camera integration
- Photo library access
- Smaller models (MobileNet only)
- Touch gestures (pinch-zoom)

## API Reference

### Canvas Engine

```typescript
class CanvasEngine {
  addElement(element: Element): void;
  removeElement(id: string): void;
  updateElement(id: string, props: Partial<Element>): void;
  exportToPNG(options: ExportOptions): Blob;
}
```

### AI Engine

```typescript
class DesignAI {
  async init(): Promise<void>;
  async suggestLayout(elements: Element[]): Promise<Suggestion[]>;
  async generatePalette(baseColor: string): Promise<string[]>;
  async classifyImage(image: Blob): Promise<string>;
}
```

## Development Roadmap

- [x] Basic canvas editor
- [x] Shape tools (rectangle, circle, text)
- [x] Template library
- [x] Local storage
- [ ] AI layout suggestions
- [ ] Font pairing AI
- [ ] Real-time collaboration
- [ ] Cloud sync (optional)

## License

MIT

## Contributing

Pull requests welcome! See CONTRIBUTING.md for guidelines.
