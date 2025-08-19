# Yukiicollectionimport React from "react"; import { motion } from "framer-motion"; import { ShoppingBag, Shirt, Pants, Search, ChevronDown, Phone, Mail, MapPin, Star, Instagram, Facebook, Globe } from "lucide-react"; import { Button } from "@/components/ui/button"; import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card"; import { Input } from "@/components/ui/input"; import { Textarea } from "@/components/ui/textarea";

// --- Brand Colors & Helpers --- const gradient = "bg-gradient-to-r from-fuchsia-600 via-rose-500 to-indigo-600"; const textGradient = "bg-gradient-to-r from-fuchsia-600 via-rose-500 to-indigo-600 bg-clip-text text-transparent";

// --- Logo (inline SVG fallback). Replace with your actual logo image if you have one --- const Logo = () => (

  <div className="flex items-center gap-3">
    <div className={`p-[2px] rounded-full ${gradient}`}>
      <div className="bg-white rounded-full p-3">
        <div className="w-10 h-10 flex items-center justify-center">
          {/* Shirt & Pants pictogram */}
          <svg viewBox="0 0 64 64" className="w-10 h-10">
            <defs>
              <linearGradient id="yukiiGrad" x1="0%" y1="0%" x2="100%" y2="0%">
                <stop offset="0%" stopColor="#d946ef" />
                <stop offset="50%" stopColor="#f43f5e" />
                <stop offset="100%" stopColor="#4f46e5" />
              </linearGradient>
            </defs>
            <path d="M20 14l6-4h12l6 4v14H20V14z" fill="none" stroke="url(#yukiiGrad)" strokeWidth="3" strokeLinecap="round" strokeLinejoin="round"/>
            <path d="M22 28h8v22H22zM34 28h8v22h-8z" fill="none" stroke="url(#yukiiGrad)" strokeWidth="3" strokeLinejoin="round"/>
          </svg>
        </div>
      </div>
    </div>
    <div>
      <div className={`text-2xl font-extrabold tracking-tight ${textGradient}`}>Yukii Collection</div>
      <div className="text-xs text-muted-foreground -mt-1">Apparel • Shirts • Pants</div>
    </div>
  </div>
);// --- Dummy product data --- const products = [ { id: 1, name: "Classic Oxford Shirt", price: 1299, tag: "New", rating: 4.7 }, { id: 2, name: "Slim Fit Denim", price: 1599, tag: "Best", rating: 4.8 }, { id: 3, name: "Casual Cotton Tee", price: 699, tag: "Hot", rating: 4.6 }, { id: 4, name: "Chino Pants", price: 1399, tag: "New", rating: 4.5 }, { id: 5, name: "Linen Summer Shirt", price: 1499, tag: "Eco", rating: 4.9 }, { id: 6, name: "Tailored Trousers", price: 1899, tag: "Premium", rating: 4.8 }, ];

export default function YukiiCollectionSite() { const [query, setQuery] = React.useState(""); const [sort, setSort] = React.useState("popular");

const filtered = products .filter((p) => p.name.toLowerCase().includes(query.toLowerCase())) .sort((a, b) => { if (sort === "priceLow") return a.price - b.price; if (sort === "priceHigh") return b.price - a.price; if (sort === "rating") return b.rating - a.rating; return b.rating - a.rating; // popular fallback });

return ( <div className="min-h-screen bg-neutral-50 text-neutral-900"> {/* Topbar */} <header className="sticky top-0 z-40 backdrop-blur bg-white/80 border-b"> <div className="max-w-6xl mx-auto px-4 py-3 flex items-center justify-between"> <Logo /> <nav className="hidden md:flex items-center gap-6 text-sm"> <a href="#shop" className="hover:underline">Shop</a> <a href="#about" className="hover:underline">About</a> <a href="#testimonials" className="hover:underline">Reviews</a> <a href="#contact" className="hover:underline">Contact</a> </nav> <Button className={${gradient} text-white shadow-md shadow-rose-100}> <ShoppingBag className="w-4 h-4 mr-2"/> Shop Now</Button> </div> </header>

{/* Hero */}
  <section className="relative overflow-hidden">
    <div className={`absolute inset-0 opacity-10 ${gradient}`}></div>
    <div className="max-w-6xl mx-auto px-4 py-16 grid md:grid-cols-2 gap-10 items-center">
      <motion.div initial={{opacity:0, y:20}} whileInView={{opacity:1, y:0}} transition={{duration:0.6}} viewport={{once:true}}>
        <h1 className="text-4xl md:text-6xl font-extrabold leading-tight">
          Elevate Your <span className={textGradient}>Everyday Style</span>
        </h1>
        <p className="mt-4 text-neutral-600 max-w-prose">
          Yukii Collection – premium shirts & pants with a colourful royal touch. Crafted for comfort, tailored for confidence.
        </p>
        <div className="mt-6 flex flex-wrap gap-3">
          <Button className={`${gradient} text-white`}>Explore Collection</Button>
          <Button variant="outline">View Lookbook</Button>
        </div>
        <div className="mt-6 flex items-center gap-6 text-sm text-neutral-600">
          <div className="flex items-center gap-2"><Shirt className="w-4 h-4"/> Quality Shirts</div>
          <div className="flex items-center gap-2"><Pants className="w-4 h-4"/> Perfect Fit Pants</div>
          <div className="flex items-center gap-2"><Star className="w-4 h-4"/> 4.8/5 Rated</div>
        </div>
      </motion.div>
      <motion.div initial={{opacity:0, scale:0.95}} whileInView={{opacity:1, scale:1}} transition={{duration:0.6, delay:0.1}} viewport={{once:true}}>
        <Card className="rounded-2xl shadow-xl">
          <CardContent className="p-0">
            {/* Image Placeholder */}
            <div className="aspect-[4/3] w-full bg-white flex items-center justify-center rounded-2xl">
              <div className="text-center p-6">
                <div className={`text-3xl font-bold ${textGradient}`}>Your Product Banner</div>
                <p className="text-sm text-neutral-500 mt-2">Replace with model shots or flat-lay images.</p>
              </div>
            </div>
          </CardContent>
        </Card>
      </motion.div>
    </div>
  </section>

  {/* Shop Controls */}
  <section id="shop" className="max-w-6xl mx-auto px-4 py-10">
    <div className="flex flex-col md:flex-row md:items-center gap-3 md:gap-6 justify-between">
      <div className="flex-1 flex items-center gap-2">
        <div className="relative flex-1">
          <Search className="w-4 h-4 absolute left-3 top-1/2 -translate-y-1/2 text-neutral-400"/>
          <Input value={query} onChange={(e)=>setQuery(e.target.value)} placeholder="Search shirts, pants..." className="pl-9 rounded-2xl"/>
        </div>
      </div>
      <div className="flex items-center gap-2">
        <Button variant="outline" className="rounded-2xl" onClick={()=>setSort("rating")}>
          Sort by Rating <ChevronDown className="w-4 h-4 ml-2"/>
        </Button>
        <Button variant="outline" className="rounded-2xl" onClick={()=>setSort("priceLow")}>
          Price: Low to High
        </Button>
        <Button variant="outline" className="rounded-2xl" onClick={()=>setSort("priceHigh")}>
          Price: High to Low
        </Button>
      </div>
    </div>

    {/* Products Grid */}
    <div className="mt-8 grid sm:grid-cols-2 lg:grid-cols-3 gap-6">
      {filtered.map((p) => (
        <Card key={p.id} className="rounded-2xl hover:shadow-lg transition-shadow">
          <CardHeader>
            <CardTitle className="flex items-center justify-between">
              <span>{p.name}</span>
              <span className={`text-xs px-2 py-1 rounded-full ${gradient} text-white`}>{p.tag}</span>
            </CardTitle>
          </CardHeader>
          <CardContent>
            <div className="aspect-[4/3] bg-neutral-100 rounded-xl mb-4"></div>
            <div className="flex items-center justify-between">
              <div className="font-semibold">₹{p.price}</div>
              <div className="flex items-center gap-1 text-sm text-amber-500">
                <Star className="w-4 h-4 fill-current"/> {p.rating}
              </div>
            </div>
            <Button className={`w-full mt-4 ${gradient} text-white`}>Add to Cart</Button>
          </CardContent>
        </Card>
      ))}
    </div>
  </section>

  {/* About */}
  <section id="about" className="max-w-6xl mx-auto px-4 py-16">
    <div className="grid md:grid-cols-2 gap-10 items-center">
      <div>
        <h2 className="text-3xl md:text-4xl font-extrabold">About <span className={textGradient}>Yukii</span></h2>
        <p className="mt-4 text-neutral-600">
          We blend minimalist design with royal, colourful accents. From everyday tees to tailored trousers, our pieces are made with breathable fabrics and mindful cuts.
        </p>
        <ul className="mt-6 grid grid-cols-2 gap-4 text-sm">
          <li className="bg-white border rounded-2xl p-4">Premium Fabrics</li>
          <li className="bg-white border rounded-2xl p-4">Perfect Tailoring</li>
          <li className="bg-white border rounded-2xl p-4">Made for India</li>
          <li className="bg-white border rounded-2xl p-4">Hassle-free Returns</li>
        </ul>
      </div>
      <div>
        <Card className="rounded-2xl">
          <CardContent className="p-6">
            <div className="aspect-[4/3] rounded-xl bg-neutral-100"></div>
            <p className="text-sm text-neutral-500 mt-3">Drop your brand story image or manufacturing shot here.</p>
          </CardContent>
        </Card>
      </div>
    </div>
  </section>

  {/* Testimonials */}
  <section id="testimonials" className="max-w-6xl mx-auto px-4 py-16">
    <h2 className="text-3xl md:text-4xl font-extrabold text-center">What Customers Say</h2>
    <div className="mt-8 grid md:grid-cols-3 gap-6">
      {["Great fit & quality!", "Colours are 🔥 and premium.", "Fast delivery, awesome stitching."].map((t, i) => (
        <Card key={i} className="rounded-2xl">
          <CardContent className="p-6">
            <div className="flex items-center gap-2 text-amber-500 mb-3">
              {Array.from({length:5}).map((_,i)=>(<Star key={i} className="w-4 h-4 fill-current"/>))}
            </div>
            <p className="text-neutral-700">{t}</p>
          </CardContent>
        </Card>
      ))}
    </div>
  </section>

  {/* Contact */}
  <section id="contact" className="max-w-6xl mx-auto px-4 py-16">
    <div className="grid md:grid-cols-2 gap-10">
      <div>
        <h2 className="text-3xl md:text-4xl font-extrabold">Get in Touch</h2>
        <p className="mt-2 text-neutral-600">Wholesale, collaborations, or customer support—send us a message.</p>
        <div className="mt-6 space-y-3 text-sm text-neutral-700">
          <div className="flex items-center gap-2"><Phone className="w-4 h-4"/> +91-90000-00000</div>
          <div className="flex items-center gap-2"><Mail className="w-4 h-4"/> hello@yukiicollection.com</div>
          <div className="flex items-center gap-2"><MapPin className="w-4 h-4"/> Jaipur, Rajasthan</div>
          <div className="flex items-center gap-2"><Globe className="w-4 h-4"/> www.yukiicollection.com</div>
        </div>
      </div>
      <Card className="rounded-2xl">
        <CardHeader>
          <CardTitle>Send a Message</CardTitle>
        </CardHeader>
        <CardContent className="space-y-3">
          <Input placeholder="Your Name" className="rounded-2xl"/>
          <Input placeholder="Email or Phone" className="rounded-2xl"/>
          <Textarea placeholder="Message" className="rounded-2xl min-h-[120px]"/>
          <Button className={`${gradient} text-white w-full rounded-2xl`}>Submit</Button>
        </CardContent>
      </Card>
    </div>
  </section>

  {/* Newsletter */}
  <section className="max-w-6xl mx-auto px-4 py-16">
    <Card className="rounded-2xl">
      <CardContent className="p-6 md:p-10">
        <div className="grid md:grid-cols-2 gap-6 items-center">
          <div>
            <h3 className="text-2xl font-bold">Get new drops & offers</h3>
            <p className="text-neutral-600 mt-1">Sign up for the Yukii newsletter.</p>
          </div>
          <div className="flex gap-3">
            <Input placeholder="Enter your email" className="rounded-2xl"/>
            <Button className={`${gradient} text-white rounded-2xl`}>Subscribe</Button>
          </div>
        </div>
      </CardContent>
    </Card>
  </section>

  {/* Footer */}
  <footer className="border-t bg-white">
    <div className="max-w-6xl mx-auto px-4 py-10 grid md:grid-cols-4 gap-8 text-sm">
      <div>
        <Logo />
        <p className="mt-3 text-neutral-600">Colourful • Royal • Everyday Wear</p>
      </div>
      <div>
        <div className="font-semibold mb-3">Shop</div>
        <ul className="space-y-2 text-neutral-600">
          <li>Shirts</li>
          <li>Pants</li>
          <li>Combos</li>
          <li>Gift Cards</li>
        </ul>
      </div>
      <div>
        <div className="font-semibold mb-3">Support</div>
        <ul className="space-y-2 text-neutral-600">
          <li>FAQs</li>
          <li>Shipping & Returns</li>
          <li>Size Guide</li>
          <li>Contact</li>
        </ul>
      </div>
      <div>
        <div className="font-semibold mb-3">Follow</div>
        <div className="flex gap-3 text-neutral-600">
          <a><Instagram className="w-5 h-5"/></a>
          <a><Facebook className="w-5 h-5"/></a>
        </div>
      </div>
    </div>
    <div className="text-center text-xs text-neutral-500 py-5">© {new Date().getFullYear()} Yukii Collection. All rights reserved.</div>
  </footer>
</div>

); }


