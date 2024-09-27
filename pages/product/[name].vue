<!--
  This example requires some changes to your config:

  ```
  // tailwind.config.js
  module.exports = {
    // ...
    plugins: [
      // ...
      require('@tailwindcss/typography'),
      require('@tailwindcss/aspect-ratio'),
    ],
  }
  ```
-->
<template>
  <div class="bg-slate-900 text-white jacquard-12-regular">
    <div class="mx-auto max-w-2xl px-4 py-16 sm:px-6 sm:py-24 lg:max-w-7xl lg:px-8">
      <div class="lg:grid lg:grid-cols-2 lg:items-start lg:gap-x-8">
        <!-- Image gallery -->
        <TabGroup as="div" class="flex flex-col-reverse">
          <!-- Image selector -->

          <TabPanels class="aspect-h-1 aspect-w-1 w-full rounded-lg" :class="product.colors[0].bgColor + ' ' + product.hueColor">
            <TabPanel v-for="image in product.images" :key="image.id">
              <nuxt-img width="800" heigth="800" :src="image.src" :alt="image.alt" class="h-full w-full object-cover object-center sm:rounded-lg"/>
            </TabPanel>
          </TabPanels>
        </TabGroup>

        <!-- Product info -->
        <div class="mt-10 px-4 sm:mt-16 sm:px-0 lg:mt-0">
          <h1 class="text-4xl lg:text-5xl font-bold tracking-tight text-white">{{ product.name }}</h1>

          <div class="mt-3">
            <h2 class="sr-only">Product information</h2>
            <p class="text-4xl lg:text-5xl tracking-tight text-white">{{ product.price }}</p>
          </div>

          <!-- Reviews -->
          <div class="mt-3">
            <h3 class="sr-only">Reviews</h3>
            <div class="flex items-center">
              <div class="flex items-center">
                <StarIcon v-for="rating in [0, 1, 2, 3, 4]" :key="rating" :class="[product.rating > rating ? 'text-indigo-500' : 'text-gray-100', 'h-8 w-8 flex-shrink-0']" aria-hidden="true" />
              </div>
              <p class="sr-only">{{ product.rating }} out of 5 stars</p>
            </div>
          </div>

          <div class="mt-6">
            <h3 class="sr-only">Description</h3>

            <div class="space-y-6 text-2xl text-gray-200" v-html="product.description" />
          </div>

          <form class="mt-6">
            <!-- Colors -->
            <div>
              <h3 class="text-3xl font-medium text-gray-300">Flavor</h3>

              <fieldset aria-label="Choose a color" class="mt-2">
                <div class="flex items-center space-x-3">
                  <nuxt-link
                      v-for="(p, i) in products[route.params.name as string]"
                      :key="i"
                      :to="{ name: 'product-name', params: { name: route.params.name }, query: { index: i } }"
                      class="rounded-full border-2 w-8 h-8 flex items-center justify-center"
                      :class="((route.query.index ? parseInt(route.query.index as string) : 0) == i ? 'border-white ' : 'border-slate-950 ') + p.colors[0].bgColor + ' ' + p.hueColor"
                  >
                  </nuxt-link>
                </div>
              </fieldset>
            </div>
          </form>

          <section aria-labelledby="details-heading" class="mt-12">
            <h2 id="details-heading" class="sr-only">Additional details</h2>

            <div class="divide-y divide-gray-200 border-t">
              <Disclosure as="div" v-for="detail in product.details" :key="detail.name" v-slot="{ open }">
                <h3>
                  <DisclosureButton class="group relative flex w-full items-center justify-between py-6 text-left">
                    <span :class="[open ? 'text-indigo-500' : 'text-gray-300', 'text-3xl font-medium']">{{ detail.name }}</span>
                    <span class="ml-6 flex items-center">
                      <PlusIcon v-if="!open" class="block h-6 w-6 text-gray-400 group-hover:text-gray-500" aria-hidden="true" />
                      <MinusIcon v-else class="block h-6 w-6 text-indigo-400 group-hover:text-indigo-500" aria-hidden="true" />
                    </span>
                  </DisclosureButton>
                </h3>
                <DisclosurePanel as="div" class="prose prose-sm pb-6 text-xl">
                  <ul v-if="detail.items.length > 1" role="list">
                    <li v-for="item in detail.items" :key="item">{{ item }}</li>
                  </ul>
                  <p v-else>{{ detail.items[0] }}</p>
                </DisclosurePanel>
              </Disclosure>
            </div>
          </section>
        </div>
      </div>
    </div>
    <div class="flex items-center justify-center pb-32">
      <div class="w-4/5 lg:w-3/5">
        <h2 class="sr-only">Customer Reviews</h2>

        <div class="-my-10">
          <div v-for="(review, reviewIdx) in product.notes" :key="reviewIdx" class="flex space-x-4 text-sm text-gray-500">
            <div class="flex-none py-10">
              <nuxt-img width="64" heigth="64" :src="'https://api.dicebear.com/9.x/micah/svg?seed=' + review.user" :alt="review.user + ' Profil picture'" class="h-16 w-16 rounded-full bg-gray-100" />
            </div>
            <div :class="[reviewIdx === 0 ? '' : 'border-t border-gray-200', 'flex-1 py-10']">
              <h3 class="font-medium text-2xl text-white">{{ review.user }}</h3>
              <p>
                <time class="text-xl text-gray-100" :datetime="review.date">{{ review.date }}</time>
              </p>

              <div class="mt-4 flex items-center">
                <StarIcon v-for="rating in [0, 1, 2, 3, 4]" :key="rating" :class="[review.rating > rating ? 'text-yellow-400' : 'text-gray-300', 'h-5 w-5 flex-shrink-0']" aria-hidden="true" />
              </div>
              <p class="sr-only">{{ review.rating }} out of 5 stars</p>

              <div class="prose prose-sm mt-4 max-w-none text-gray-100 text-xl" v-html="review.commentary" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import {
  Disclosure,
  DisclosureButton,
  DisclosurePanel,
  TabGroup,
  TabPanel,
  TabPanels,
} from '@headlessui/vue'
import { StarIcon } from '@heroicons/vue/20/solid'
import { MinusIcon, PlusIcon } from '@heroicons/vue/24/outline'

interface Product {
  name: string
  price: string
  rating: number
  images: { id: number; name: string; src: string; alt: string }[]
  colors: { name: string; bgColor: string; selectedColor: string }[]
  description: string
  details: { name: string; items: string[] }[]
  notes: { rating: number; commentary: string; user: string; date: string }[],
  hueColor: string,
  meta : {
    title: string,
    description: string,
    keywords: string
  }
}


const products: Record<string, Product[]> = {
  "arasboost": [
    {
      "name": "Original ArasBoost",
      "price": "$3.99",
      "rating": 4,
      "meta": {
        "title": "Arasgrasa Energy Shot - Original ArasBoost for Instant Vitality",
        "description": "Experience the Original ArasBoost, an energy shot made with Arasgrasa and ancient herbs for a fast, natural energy boost. Perfect for intense tasks.",
        "keywords": "Arasgrasa, ArasBoost, energy shot, natural energy, herbal energy, instant energy, elvish vitality, Arasgrasa drink"
      },
      "hueColor": "hue-rotate-0",
      "images": [
        {
          "id": 1,
          "name": "Original ArasBoost Image",
          "src": "/ArasBoost-transparant.webp",
          "alt": "Original ArasBoost image."
        }
      ],
      "colors": [
        {
          "name": "Amber",
          "bgColor": "bg-gradient-to-br from-amber-700 to-yellow-500",
          "selectedColor": "ring-amber-700"
        }
      ],
      "description": "<p>A concentrated elvish energy shot made from Arasgrasa and a mix of ancient herbal extracts. Provides an instant surge of vitality for intense physical or magical tasks.</p>",
      "details": [
        {
          "name": "Ingredients",
          "items": [
            "Concentrated Arasgrasa Extract",
            "Herbal Blend (Ginkgo Biloba, Echinacea, Elderberry)",
            "Peppermint Extract",
            "Organic Agave Nectar",
            "Natural Caffeine",
            "Ginger Root Extract",
            "Pure Spring Water",
            "Vitamin B Complex"
          ]
        },
        {
          "name": "Flavor Profile",
          "items": ["Herbal with a hint of peppermint and ginger."]
        },
        {
          "name": "Benefits",
          "items": ["Instant energy, focus enhancement, and stamina boost."]
        }
      ],
      "notes": [
        {
          "rating": 5,
          "commentary": "Amazing energy boost without any jitters. Perfect for my morning rituals!",
          "user": "Elven Healer",
          "date": "2024-01-05"
        },
        {
          "rating": 4,
          "commentary": "Strong and effective, but I wish it was a bit sweeter.",
          "user": "Elven Warrior",
          "date": "2024-02-10"
        }
      ]
    },
    {
      "name": "Citrus Burst ArasBoost",
      "price": "$3.99",
      "rating": 4.5,
      "meta": {
        "title": "Citrus Arasgrasa Energy Shot - Citrus Burst ArasBoost",
        "description": "Revitalize with Citrus Burst ArasBoost, an Arasgrasa energy shot infused with lemon and orange for a refreshing, quick recharge.",
        "keywords": "Arasgrasa, Citrus Burst, ArasBoost, citrus energy drink, natural energy, herbal energy shot, instant vitality, Arasgrasa citrus drink"
      },
      "hueColor": "hue-rotate-90",
      "images": [
        {
          "id": 1,
          "name": "Citrus Burst ArasBoost Image",
          "src": "/ArasBoost-transparant.webp",
          "alt": "Citrus Burst ArasBoost image."
        }
      ],
      "colors": [
        {
          "name": "Amber",
          "bgColor": "bg-gradient-to-br from-amber-700 to-yellow-500",
          "selectedColor": "ring-amber-700"
        }
      ],
      "description": "<p>An invigorating version of ArasBoost featuring citrus fruits for a refreshing energy lift. Perfect for elves needing a zesty, quick recharge.</p>",
      "details": [
        {
          "name": "Ingredients",
          "items": [
            "Concentrated Arasgrasa Extract",
            "Herbal Blend (Ginkgo Biloba, Echinacea, Elderberry)",
            "Lemon Zest Extract",
            "Orange Peel Extract",
            "Natural Caffeine",
            "Ginger Root Extract",
            "Pure Spring Water",
            "Organic Agave Nectar"
          ]
        },
        {
          "name": "Flavor Profile",
          "items": ["Zesty with notes of lemon and orange."]
        },
        {
          "name": "Benefits",
          "items": ["Refreshing, quick energy boost, and increased alertness."]
        }
      ],
      "notes": [
        {
          "rating": 4,
          "commentary": "Great citrus flavor! Gives a nice energy lift without the crash.",
          "user": "Elven Scout",
          "date": "2024-01-15"
        },
        {
          "rating": 5,
          "commentary": "The best energy shot I've tried. Love the refreshing taste!",
          "user": "Elven Artist",
          "date": "2024-02-01"
        }
      ]
    },
    {
      "name": "Herbal Bliss ArasBoost",
      "price": "$3.99",
      "rating": 4,
      "hueColor": "hue-rotate-180",
      "meta": {
        "title": "Herbal Arasgrasa Energy Shot - Herbal Bliss ArasBoost",
        "description": "Find balance with Herbal Bliss ArasBoost, a soothing Arasgrasa energy shot. Ideal for creative tasks, offering a calm yet focused energy boost.",
        "keywords": "Arasgrasa, Herbal Bliss, ArasBoost, herbal energy shot, natural energy, calm energy, balanced energy drink, Arasgrasa herbal drink"
      },
      "images": [
        {
          "id": 1,
          "name": "Herbal Bliss ArasBoost Image",
          "src": "/ArasBoost-transparant.webp",
          "alt": "Herbal Bliss ArasBoost image."
        }
      ],
      "colors": [
        {
          "name": "Amber",
          "bgColor": "bg-gradient-to-br from-amber-700 to-yellow-500",
          "selectedColor": "ring-amber-700"
        }
      ],
      "description": "<p>A balanced version of ArasBoost with calming herbs. Ideal for those who seek a gentle, focused energy lift during creative or spiritual tasks.</p>",
      "details": [
        {
          "name": "Ingredients",
          "items": [
            "Concentrated Arasgrasa Extract",
            "Chamomile Extract",
            "Lemon Balm",
            "Peppermint Extract",
            "Lavender Essence",
            "Natural Caffeine",
            "Pure Spring Water",
            "Stevia Leaf Extract"
          ]
        },
        {
          "name": "Flavor Profile",
          "items": ["Soothing herbal notes with a hint of peppermint."]
        },
        {
          "name": "Benefits",
          "items": ["Balanced energy, enhanced focus, and calming effect."]
        }
      ],
      "notes": [
        {
          "rating": 4,
          "commentary": "Provides a balanced energy boost, perfect for meditation.",
          "user": "Elven Druid",
          "date": "2024-01-25"
        },
        {
          "rating": 5,
          "commentary": "Love the herbal blend. It helps me stay calm and focused.",
          "user": "Elven Healer",
          "date": "2024-02-05"
        }
      ]
    }
  ],
  "sylvansurge": [
    {
      "name": "Original Sylvan Surge",
      "price": "$4.99",
      "rating": 5,
      "meta": {
        "title": "Arasgrasa Herbal Energy Tea - Original Sylvan Surge",
        "description": "Discover the original Sylvan Surge, an Arasgrasa-infused herbal energy tea. Perfect for natural relaxation and a steady energy boost, crafted for elves seeking balance.",
        "keywords": "Arasgrasa, Sylvan Surge, Arasgrasa tea, Arasgrasa herbal energy, elvish energy drink, herbal tea for energy, natural energy boost"
      },
      "hueColor": "hue-rotate-0",
      "images": [
        {
          "id": 1,
          "name": "Original Sylvan Surge Image",
          "src": "/SylvanSurge-transparant.webp",
          "alt": "Original Sylvan Surge image."
        }
      ],
      "colors": [
        {
          "name": "Green",
          "bgColor": "bg-gradient-to-br from-green-800 to-amber-700",
          "selectedColor": "ring-green-800"
        }
      ],
      "description": "<p>An elvish herbal tea that combines Arasgrasa with handpicked flowers. Offers both relaxation and an energy lift with every sip, channeling the earth's energy.</p>",
      "details": [
        {
          "name": "Ingredients",
          "items": [
            "Arasgrasa Leaf Extract",
            "Chamomile Flowers",
            "Lavender Buds",
            "Peppermint Leaves",
            "Lemon Balm",
            "Hibiscus Petals",
            "Lemongrass Stalks",
            "Natural Stevia Leaf"
          ]
        },
        {
          "name": "Flavor Profile",
          "items": ["Floral and minty with a hint of lemon."]
        },
        {
          "name": "Benefits",
          "items": ["Relaxation, natural energy boost, and focus enhancement."]
        }
      ],
      "notes": [
        {
          "rating": 5,
          "commentary": "This tea is soothing and provides a gentle energy boost. Love it!",
          "user": "Elven Healer",
          "date": "2024-02-08"
        },
        {
          "rating": 4,
          "commentary": "Great flavor and calming effect, but could be a bit stronger.",
          "user": "Elven Scholar",
          "date": "2024-03-01"
        }
      ]
    },
    {
      "name": "Forest Berry Sylvan Surge",
      "price": "$4.99",
      "rating": 5,
      "meta": {
        "title": "Arasgrasa Herbal Tea - Forest Berry Sylvan Surge",
        "description": "Enjoy Forest Berry Sylvan Surge, a delicious Arasgrasa energy tea with rich blackberry and raspberry flavors. A fruity way to energize and relax.",
        "keywords": "Arasgrasa, Sylvan Surge, forest berry Arasgrasa tea, berry herbal tea, natural energy drink, Arasgrasa berry tea, herbal tea for energy"
      },
      "hueColor": "hue-rotate-180",
      "images": [
        {
          "id": 1,
          "name": "Forest Berry Sylvan Surge Image",
          "src": "/SylvanSurge-transparant.webp",
          "alt": "Forest Berry Sylvan Surge image."
        }
      ],
      "colors": [
        {
          "name": "Green",
          "bgColor": "bg-gradient-to-br from-green-800 to-amber-700",
          "selectedColor": "ring-green-800"
        }
      ],
      "description": "<p>A berry-infused version of Sylvan Surge featuring dried blackberries and raspberries. Offers a rich, fruity tea experience with added vitality.</p>",
      "details": [
        {
          "name": "Ingredients",
          "items": [
            "Arasgrasa Leaf Extract",
            "Dried Blackberries",
            "Dried Raspberries",
            "Juniper Berries",
            "Chamomile Flowers",
            "Hibiscus Petals",
            "Lemongrass Stalks",
            "Natural Stevia Leaf"
          ]
        },
        {
          "name": "Flavor Profile",
          "items": ["Rich, fruity with subtle floral undertones."]
        },
        {
          "name": "Benefits",
          "items": ["Boosts energy, improves mood, and promotes relaxation."]
        }
      ],
      "notes": [
        {
          "rating": 5,
          "commentary": "Delicious berry flavor! Perfect for a refreshing afternoon break.",
          "user": "Elven Gardener",
          "date": "2024-02-15"
        },
        {
          "rating": 4,
          "commentary": "Nice flavor, but I prefer the original for its calming effects.",
          "user": "Elven Herbalist",
          "date": "2024-02-22"
        }
      ]
    },
    {
      "name": "Peach Blossom Sylvan Surge",
      "price": "$4.99",
      "rating": 4.5,
      "meta": {
        "title": "Arasgrasa Tea - Peach Blossom Sylvan Surge for Energy",
        "description": "Rejuvenate with Peach Blossom Sylvan Surge, an Arasgrasa-infused herbal tea with the sweet aroma of peach blossoms. Perfect for energy and relaxation.",
        "keywords": "Arasgrasa, Sylvan Surge, peach blossom Arasgrasa tea, peach herbal tea, natural energy drink, Arasgrasa peach tea, herbal energy drink"
      },
      "hueColor": "hue-rotate-90",
      "images": [
        {
          "id": 1,
          "name": "Peach Blossom Sylvan Surge Image",
          "src": "/SylvanSurge-transparant.webp",
          "alt": "Peach Blossom Sylvan Surge image."
        }
      ],
      "colors": [
        {
          "name": "Green",
          "bgColor": "bg-gradient-to-br from-green-800 to-amber-700",
          "selectedColor": "ring-green-800"
        }
      ],
      "description": "<p>A refreshing blend of Arasgrasa and sweet peach blossoms, offering a delightful twist for a rejuvenating tea experience.</p>",
      "details": [
        {
          "name": "Ingredients",
          "items": [
            "Arasgrasa Leaf Extract",
            "Dried Peach Blossoms",
            "Chamomile Flowers",
            "Peppermint Leaves",
            "Natural Stevia Leaf",
            "Lemon Zest"
          ]
        },
        {
          "name": "Flavor Profile",
          "items": ["Sweet and floral with a hint of mint."]
        },
        {
          "name": "Benefits",
          "items": ["Hydration, mood enhancement, and refreshing energy."]
        }
      ],
      "notes": [
        {
          "rating": 5,
          "commentary": "A lovely blend! The peach flavor is delightful.",
          "user": "Elven Artisan",
          "date": "2024-02-10"
        },
        {
          "rating": 4,
          "commentary": "Very refreshing, but I wish it had a stronger peach flavor.",
          "user": "Elven Botanist",
          "date": "2024-02-18"
        }
      ]
    }
  ],
  "elvenspark": [
    {
      "name": "Original ElvenSpark",
      "price": "$2.99",
      "rating": 5,
      "meta": {
        "title": "Original ElvenSpark - Arasgrasa Energy Drink for Steady Energy Boost",
        "description": "Experience Original ElvenSpark, a premium Arasgrasa-based energy drink designed for elven warriors and adventurers. Long-lasting energy with no crash, made from natural ingredients.",
        "keywords": "Arasgrasa, Original ElvenSpark, arasgrasa energy drink, arasgrasa product, elven energy boost, natural energy drink, elven warriors drink"
      },
      "hueColor": "hue-rotate-0",
      "images": [
        {
          "id": 1,
          "name": "Original ElvenSpark Image",
          "src": "/ElvenSpark-transparant.webp",
          "alt": "Original ElvenSpark image."
        }
      ],
      "colors": [
        {
          "name": "Gradient",
          "bgColor": "bg-gradient-to-br from-rose-500 to-yellow-600",
          "selectedColor": "ring-rose-500"
        }
      ],
      "description": "<p>A vibrant, glowing energy drink designed for elven warriors and travelers. Provides a long-lasting, steady energy boost without the crash.</p>",
      "details": [
        {
          "name": "Ingredients",
          "items": [
            "Arasgrasa Extract",
            "Honey from Enchanted Flowers",
            "Fresh River Water",
            "Green Tea Extract",
            "Natural Caffeine",
            "Lemon Zest",
            "Ginseng Root Extract",
            "Electrolytes Blend"
          ]
        },
        {
          "name": "Flavor Profile",
          "items": ["Crisp, refreshing with a hint of citrus and honey."]
        },
        {
          "name": "Benefits",
          "items": ["Sustained energy, hydration, and focus enhancement."]
        }
      ],
      "notes": [
        {
          "rating": 5,
          "commentary": "Provides a great energy boost without the crash. Tastes amazing!",
          "user": "Elven Warrior",
          "date": "2024-02-12"
        },
        {
          "rating": 4,
          "commentary": "Love the natural ingredients, but wish it was a bit less sweet.",
          "user": "Elven Athlete",
          "date": "2024-02-20"
        }
      ]
    },
    {
      "name": "Citrus ElvenSpark",
      "price": "$2.99",
      "rating": 4.5,
      "meta": {
        "title": "Citrus ElvenSpark - Arasgrasa Energy Drink with Zesty Flavor",
        "description": "Citrus ElvenSpark, a refreshing Arasgrasa-based energy drink with a burst of citrus flavors. Ideal for keeping you sharp and energized on hot days.",
        "keywords": "Arasgrasa, Citrus ElvenSpark, arasgrasa energy drink, citrus flavor energy drink, natural energy drink, arasgrasa product"
      },
      "hueColor": "hue-rotate-90",
      "images": [
        {
          "id": 1,
          "name": "Citrus ElvenSpark Image",
          "src": "/ElvenSpark-transparant.webp",
          "alt": "Citrus ElvenSpark image."
        }
      ],
      "colors": [
        {
          "name": "Gradient",
          "bgColor": "bg-gradient-to-br from-rose-500 to-yellow-600",
          "selectedColor": "ring-rose-500"
        }
      ],
      "description": "<p>A citrus-flavored variant of ElvenSpark for an extra zing of energy. Perfect for those hot summer days!</p>",
      "details": [
        {
          "name": "Ingredients",
          "items": [
            "Arasgrasa Extract",
            "Citrus Extracts (Lemon, Lime, Orange)",
            "Fresh River Water",
            "Green Tea Extract",
            "Natural Caffeine",
            "Electrolytes Blend",
            "Natural Sweetener"
          ]
        },
        {
          "name": "Flavor Profile",
          "items": ["Zesty and refreshing with a hint of sweetness."]
        },
        {
          "name": "Benefits",
          "items": ["Revitalizing, hydrating, and great for hot weather."]
        }
      ],
      "notes": [
        {
          "rating": 5,
          "commentary": "Refreshing and energizing! Perfect for my outdoor adventures.",
          "user": "Elven Scout",
          "date": "2024-02-18"
        },
        {
          "rating": 4,
          "commentary": "I enjoyed the flavor but found it a bit too sweet for my taste.",
          "user": "Elven Archer",
          "date": "2024-02-28"
        }
      ]
    },
    {
      "name": "Berry ElvenSpark",
      "price": "$2.99",
      "rating": 4.8,
      "meta": {
        "title": "Berry ElvenSpark - Arasgrasa Energy Drink with Fruity Flavor",
        "description": "Berry ElvenSpark, a deliciously fruity variant of the Arasgrasa-based energy drink. Offers a refreshing burst of energy with berry flavors, perfect for recovery.",
        "keywords": "Arasgrasa, Berry ElvenSpark, berry flavor energy drink, arasgrasa product, elven energy drink, natural energy boost"
      },
      "hueColor": "hue-rotate-180",
      "images": [
        {
          "id": 1,
          "name": "Berry ElvenSpark Image",
          "src": "/ElvenSpark-transparant.webp",
          "alt": "Berry ElvenSpark image."
        }
      ],
      "colors": [
        {
          "name": "Gradient",
          "bgColor": "bg-gradient-to-br from-rose-500 to-yellow-600",
          "selectedColor": "ring-rose-500"
        }
      ],
      "description": "<p>A berry-infused variant of ElvenSpark, providing a deliciously fruity flavor and an extra kick of energy.</p>",
      "details": [
        {
          "name": "Ingredients",
          "items": [
            "Arasgrasa Extract",
            "Mixed Berry Extracts (Strawberry, Raspberry, Blueberry)",
            "Fresh River Water",
            "Green Tea Extract",
            "Natural Caffeine",
            "Electrolytes Blend",
            "Natural Sweetener"
          ]
        },
        {
          "name": "Flavor Profile",
          "items": ["Fruity and refreshing with a hint of sweetness."]
        },
        {
          "name": "Benefits",
          "items": ["Energizing, hydrating, and great for post-activity recovery."]
        }
      ],
      "notes": [
        {
          "rating": 5,
          "commentary": "Best energy drink ever! The berry flavor is fantastic.",
          "user": "Elven Adventurer",
          "date": "2024-02-25"
        },
        {
          "rating": 4,
          "commentary": "Very tasty! A bit sweet, but I love the flavor.",
          "user": "Elven Explorer",
          "date": "2024-03-05"
        }
      ]
    }
  ]
}

const route = useRoute()

console.log(route.query.index)
const index = ref(route.query.index ? parseInt(route.query.index as string) : 0)

const product = computed(() => {
  const name = route.params.name as string
  return products[name][index.value]
})

useHead({
  title: product.value.meta.title,
  meta: [
    { name: 'description', content: product.value.meta.description },
    { name: 'keywords', content: product.value.meta.keywords },
  ]
})

useSchemaOrg([
  defineProduct({
    name: product.value.meta.title,
    image: product.value.images[0].src,
    description: product.value.meta.description,
    brand: 'Arasgrasa Tech',
    offers: defineOffer({
      price: product.value.price,
      priceCurrency: 'USD',
      availability: 'https://schema.org/InStock',
      url: route.fullPath
    }),
    aggregateRating: {
      ratingValue: product.value.rating.toString(),
      reviewCount: product.value.notes.length.toString(),
    },
    review: product.value.notes.map((note) => defineReview({
      reviewBody: note.commentary,
      author: {
        name: note.user,
      },
      reviewRating: {
        bestRating: "5",
        ratingValue: note.rating.toString(),
        worstRating: "1"
      }
    }))
  }),
])

watch(() => route.query.index, (value) => {
  index.value = value ? parseInt(value as string) : 0

  useHead({
    title: product.value.meta.title,
    meta: [
      { name: 'description', content: product.value.meta.description },
      { name: 'keywords', content: product.value.meta.keywords },
    ]
  })

  useSchemaOrg([
    defineProduct({
      name: product.value.meta.title,
      image: product.value.images[0].src,
      description: product.value.meta.description,
      brand: 'Arasgrasa Tech',
      offers: defineOffer({
        price: product.value.price,
        priceCurrency: 'USD',
        availability: 'https://schema.org/InStock',
        url: route.fullPath
      })
    }),
  ])
})

</script>
