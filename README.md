import React, { useState } from 'react';
import { Card, CardContent } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { ShoppingCart, Star } from 'lucide-react';
import { Instagram, Facebook } from 'lucide-react';

const products = [
  { id: 1, name: 'PC Gamer Ryzen 5', price: '$800', image: 'https://via.placeholder.com/150', rating: 4 },
  { id: 2, name: 'GTX 1660 Super', price: '$250', image: 'https://via.placeholder.com/150', rating: 5 },
  { id: 3, name: 'SSD 1TB', price: '$120', image: 'https://via.placeholder.com/150', rating: 3 },
];

const services = [
  'Reparación de PCs',
  'Mantenimiento preventivo',
  'Instalación de sistemas operativos',
  'Armado de PCs a pedido'
];

export default function SkyTecnoFix() {
  const [siteRating, setSiteRating] = useState(0);

  const handleRating = (rating) => {
    setSiteRating(rating);
  };

  return (
    <div className="min-h-screen bg-white p-6 text-gray-800">
      <header className="flex items-center justify-between py-8 bg-gradient-to-r from-blue-500 to-purple-600 text-white rounded-2xl shadow-lg px-6">
        <input type="file" accept="image/*" className="hidden" id="logo-upload" onChange={(e) => {
          const logo = document.getElementById('logo');
          logo.src = URL.createObjectURL(e.target.files[0]);
        }} />
        <label htmlFor="logo-upload" className="cursor-pointer">
          <img id="logo" src="https://via.placeholder.com/100x50" alt="SkyTecnoFix Logo" className="h-12 rounded-md" />
        </label>
        <h1 className="text-5xl font-extrabold">SkyTecnoFix</h1>
        <p className="text-xl mt-2 hidden md:block">Tu solución en tecnología</p>
      </header>

      <section className="my-12">
        <h2 className="text-3xl font-semibold text-blue-600 mb-6">Servicios</h2>
        <ul className="list-disc pl-6 space-y-3">
          {services.map((service, index) => (
            <li key={index} className="text-lg">{service}</li>
          ))}
        </ul>
      </section>

      <section className="my-12">
        <h2 className="text-3xl font-semibold text-blue-600 mb-6">Productos en Venta</h2>
        <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
          {products.map((product) => (
            <Card key={product.id} className="rounded-2xl shadow-lg border border-gray-200">
              <img src={product.image} alt={product.name} className="w-full h-48 object-cover rounded-t-2xl" />
              <CardContent className="p-5">
                <h3 className="text-2xl font-bold text-gray-900">{product.name}</h3>
                <p className="text-lg text-gray-700 mb-2">{product.price}</p>
                <div className="flex items-center mb-4">
                  {[1, 2, 3, 4, 5].map((star) => (
                    <Star key={star} size={20} className={`mr-1 ${star <= product.rating ? 'text-yellow-400' : 'text-gray-300'}`} />
                  ))}
                </div>
                <Button className="w-full flex items-center justify-center gap-2 bg-blue-600 hover:bg-blue-700 text-white">
                  <ShoppingCart size={20} /> Comprar
                </Button>
              </CardContent>
            </Card>
          ))}
        </div>
      </section>

      <section className="my-12 text-center">
        <h2 className="text-3xl font-semibold text-blue-600 mb-4">Valora Nuestra Página</h2>
        <div className="flex justify-center">
          {[1, 2, 3, 4, 5].map((star) => (
            <Star key={star} size={32} onClick={() => handleRating(star)} className={`cursor-pointer ${star <= siteRating ? 'text-yellow-400' : 'text-gray-300'}`} />
          ))}
        </div>
      </section>

      <section className="my-12">
        <h2 className="text-3xl font-semibold text-blue-600 mb-6">Anuncios</h2>
        <div className="grid grid-cols-1 sm:grid-cols-2 gap-6">
          <div className="bg-gray-200 p-4 rounded-xl shadow-md text-center">
            <p className="text-gray-700">Anuncio 1: ¡Ofertas especiales en componentes!</p>
          </div>
          <div className="bg-gray-200 p-4 rounded-xl shadow-md text-center">
            <p className="text-gray-700">Anuncio 2: Descuentos en servicios de reparación</p>
          </div>
        </div>
      </section>

      <footer className="text-center mt-16 py-6 bg-gray-100 rounded-2xl shadow-inner">
        <div className="flex justify-center space-x-6 mb-4">
          <a href="https://www.instagram.com/skytecnofix" target="_blank" rel="noopener noreferrer" className="text-pink-500 hover:text-pink-600">
            <Instagram size={28} />
          </a>
          <a href="https://www.facebook.com/skytecnofix" target="_blank" rel="noopener noreferrer" className="text-blue-600 hover:text-blue-700">
            <Facebook size={28} />
          </a>
        </div>
        <p className="text-gray-600">&copy; 2025 SkyTecnoFix. Todos los derechos reservados.</p>
      </footer>
    </div>
  );
}
