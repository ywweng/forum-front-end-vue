<template>
  <div class="container py-5">
    <NavTabs />
    <h1>最新動態</h1>
    <hr />
    <div class="row">
      <div class="col-md-6">
        <h3>最新餐廳</h3>
        <!-- 最新餐廳 NewestRestaurants -->
        <NewestRestaurants :restaurants="restaurants" />
      </div>
      <div class="col-md-6">
        <!-- 最新評論 NewestComments-->
        <h3>最新評論</h3>
        <NewestComments :comments="comments" />
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from './../components/NavTabs.vue';
import NewestRestaurants from './../components/NewestRestaurants.vue';
import NewestComments from './../components/NewestComments.vue';

const dummyData = {
  restaurants: [
    {
      id: 1,
      name: 'Johathan Jerde V',
      tel: '(557) 395-3396 x572',
      address: '70351 Gleichner Harbor',
      opening_hours: '08:00',
      description:
        'Asperiores nam accusamus. Dolorem itaque aut est. Fugiat in omnis expedita est accusantium natus.\n \rEum molestiae id recusandae mollitia consequatur nesciunt voluptates. Fugit at autem. Doloremque minima aspernatur. Facilis quidem autem ad quod. Et dignissimos repellat nihil enim et aliquam accusantium dolorum.\n \rIusto aliquam beatae dignissimos et ut voluptatum. Debitis laborum rerum possimus est. Atque doloremque iure.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=40.77230905171263',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 4,
      Category: {
        id: 4,
        name: '墨西哥料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
    },
    {
      id: 2,
      name: 'Tess Morissette PhD',
      tel: '(317) 047-8293 x6144',
      address: '5805 Clark Neck',
      opening_hours: '08:00',
      description:
        'Maiores consequuntur dolor et sunt. Deleniti tenetur fugiat dolorem et vero error alias ad et. Labore inventore saepe error aliquam. Aperiam ullam ab consequatur tenetur optio numquam magnam. Veniam autem ea laboriosam qui recusandae autem.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=99.41330214292347',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
    },
    {
      id: 3,
      name: 'Wanda Sanford',
      tel: '172-955-4446',
      address: '178 Green Point',
      opening_hours: '08:00',
      description:
        'Illo voluptatem aspernatur animi repellendus placeat sint eaque eum. Et est possimus illo facere assumenda. Saepe repellendus et quo id consequatur est eos aut. Ullam explicabo maxime dolorem magni minima neque. Voluptatibus numquam maxime nisi ducimus qui eos a.\n \rModi alias ullam sed velit cum quo cumque ab dolore. Vel doloribus impedit id ea est totam dignissimos et. Aperiam vitae ipsum omnis labore corrupti aspernatur alias corrupti. Autem magnam in autem et dolore. Dignissimos ullam at repellendus amet. Culpa alias temporibus et quasi et aperiam praesentium cupiditate soluta.\n \rAut omnis illo deserunt est. Numquam vitae earum minus veritatis exercitationem excepturi explicabo. Exercitationem voluptas quidem vitae cumque maxime quae.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=9.776075201606904',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 4,
      Category: {
        id: 4,
        name: '墨西哥料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
    },
    {
      id: 4,
      name: 'Lindsay Rowe',
      tel: '(209) 696-8084',
      address: '36024 Ona Locks',
      opening_hours: '08:00',
      description: 'Aut quo qui impedit sed.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=9.83038759675332',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
    },
    {
      id: 5,
      name: 'Idella Satterfield',
      tel: '(926) 063-2120 x581',
      address: '889 Janet Square',
      opening_hours: '08:00',
      description: 'Fuga iure quos id saepe ab itaque odit earum occaecati.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=36.78451119597441',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 1,
      Category: {
        id: 1,
        name: '中式料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
    },
    {
      id: 6,
      name: 'Angelina Quitzon I',
      tel: '811.077.2683 x24748',
      address: '1213 Nicklaus Trace',
      opening_hours: '08:00',
      description:
        'Voluptatem rem molestiae officia doloribus similique laudantium in.\nQuae ut qui non itaque minima sit cum.\nRerum eos tempore dolores eligendi totam perspiciatis ea quis.\nNihil asperiores eos distinctio non aut nisi accusantium.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=41.887010361261076',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 1,
      Category: {
        id: 1,
        name: '中式料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
    },
    {
      id: 7,
      name: 'Berneice Herzog',
      tel: '338-580-2426',
      address: '895 Mae Turnpike',
      opening_hours: '08:00',
      description:
        'Quod reiciendis itaque iure voluptas quo nulla provident modi aliquam.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=10.746556012930641',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 1,
      Category: {
        id: 1,
        name: '中式料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
    },
    {
      id: 8,
      name: 'Zena Kuhn V',
      tel: '183.919.3331',
      address: '4856 Upton Via',
      opening_hours: '08:00',
      description: 'odio',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=87.86589893032648',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 1,
      Category: {
        id: 1,
        name: '中式料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
    },
    {
      id: 9,
      name: 'Florine McLaughlin DVM',
      tel: '(790) 829-4484 x00755',
      address: '39017 Mohammad Lodge',
      opening_hours: '08:00',
      description:
        'Autem eaque sed alias nisi aut facere ipsam ut laborum. Hic nostrum vero aut rerum sit cupiditate quasi. Ullam perferendis eius nisi aut. Atque ut nisi dolore eius sed soluta magni id. Aut repudiandae quos harum deserunt nemo placeat.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=9.756850302612353',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 5,
      Category: {
        id: 5,
        name: '素食料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
    },
    {
      id: 10,
      name: 'Jolie Dibbert',
      tel: '962-209-3272 x73704',
      address: '354 Dare Dam',
      opening_hours: '08:00',
      description:
        'Aliquid ipsum laboriosam commodi. Veniam tempora distinctio hic expedita ipsam. Reiciendis quaerat aut exercitationem id est.\n \rNatus ipsam pariatur. Voluptate perspiciatis ipsum odio voluptas magni. Ipsa adipisci dolores quis aperiam.\n \rUt expedita aperiam dignissimos consequuntur deserunt rerum. Doloremque temporibus voluptas. Doloremque ipsam est occaecati perspiciatis facilis qui tempore et. Fugit eum illo perferendis omnis ut distinctio. Quos repudiandae libero et distinctio in tempore quae.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=36.11119470075997',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
    },
  ],
  comments: [
    {
      id: 1,
      text: 'Vero et est est sed accusantium consequatur iusto ipsa.',
      UserId: 3,
      RestaurantId: 1,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      User: {
        id: 3,
        name: 'user2',
        email: 'user2@example.com',
        password:
          '$2a$10$JPhaLC4JdTUH08gPRSI07esdEadoY7t1e0GGytt05hqfVeQBiNJ5i',
        isAdmin: false,
        image: null,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      Restaurant: {
        id: 1,
        name: 'Johathan Jerde V',
        tel: '(557) 395-3396 x572',
        address: '70351 Gleichner Harbor',
        opening_hours: '08:00',
        description:
          'Asperiores nam accusamus. Dolorem itaque aut est. Fugiat in omnis expedita est accusantium natus.\n \rEum molestiae id recusandae mollitia consequatur nesciunt voluptates. Fugit at autem. Doloremque minima aspernatur. Facilis quidem autem ad quod. Et dignissimos repellat nihil enim et aliquam accusantium dolorum.\n \rIusto aliquam beatae dignissimos et ut voluptatum. Debitis laborum rerum possimus est. Atque doloremque iure.',
        image:
          'https://loremflickr.com/320/240/restaurant,food/?random=40.77230905171263',
        viewCounts: 0,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
        CategoryId: 4,
      },
    },
    {
      id: 2,
      text: 'Molestias harum asperiores rerum soluta non possimus expedita illum.',
      UserId: 1,
      RestaurantId: 2,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      User: {
        id: 1,
        name: 'root',
        email: 'root@example.com',
        password:
          '$2a$10$/pXYqaEE24k4RAfLSItXfuXbDV4bNawnZwie9229hMzPEe/ZbDx3G',
        isAdmin: true,
        image: null,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      Restaurant: {
        id: 2,
        name: 'Tess Morissette PhD',
        tel: '(317) 047-8293 x6144',
        address: '5805 Clark Neck',
        opening_hours: '08:00',
        description:
          'Maiores consequuntur dolor et sunt. Deleniti tenetur fugiat dolorem et vero error alias ad et. Labore inventore saepe error aliquam. Aperiam ullam ab consequatur tenetur optio numquam magnam. Veniam autem ea laboriosam qui recusandae autem.',
        image:
          'https://loremflickr.com/320/240/restaurant,food/?random=99.41330214292347',
        viewCounts: 0,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
        CategoryId: 2,
      },
    },
    {
      id: 3,
      text: 'Dolorum sed ut magni.',
      UserId: 1,
      RestaurantId: 3,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      User: {
        id: 1,
        name: 'root',
        email: 'root@example.com',
        password:
          '$2a$10$/pXYqaEE24k4RAfLSItXfuXbDV4bNawnZwie9229hMzPEe/ZbDx3G',
        isAdmin: true,
        image: null,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      Restaurant: {
        id: 3,
        name: 'Wanda Sanford',
        tel: '172-955-4446',
        address: '178 Green Point',
        opening_hours: '08:00',
        description:
          'Illo voluptatem aspernatur animi repellendus placeat sint eaque eum. Et est possimus illo facere assumenda. Saepe repellendus et quo id consequatur est eos aut. Ullam explicabo maxime dolorem magni minima neque. Voluptatibus numquam maxime nisi ducimus qui eos a.\n \rModi alias ullam sed velit cum quo cumque ab dolore. Vel doloribus impedit id ea est totam dignissimos et. Aperiam vitae ipsum omnis labore corrupti aspernatur alias corrupti. Autem magnam in autem et dolore. Dignissimos ullam at repellendus amet. Culpa alias temporibus et quasi et aperiam praesentium cupiditate soluta.\n \rAut omnis illo deserunt est. Numquam vitae earum minus veritatis exercitationem excepturi explicabo. Exercitationem voluptas quidem vitae cumque maxime quae.',
        image:
          'https://loremflickr.com/320/240/restaurant,food/?random=9.776075201606904',
        viewCounts: 0,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
        CategoryId: 4,
      },
    },
    {
      id: 4,
      text: 'Repellat vitae impedit rerum sed.',
      UserId: 3,
      RestaurantId: 4,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      User: {
        id: 3,
        name: 'user2',
        email: 'user2@example.com',
        password:
          '$2a$10$JPhaLC4JdTUH08gPRSI07esdEadoY7t1e0GGytt05hqfVeQBiNJ5i',
        isAdmin: false,
        image: null,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      Restaurant: {
        id: 4,
        name: 'Lindsay Rowe',
        tel: '(209) 696-8084',
        address: '36024 Ona Locks',
        opening_hours: '08:00',
        description: 'Aut quo qui impedit sed.',
        image:
          'https://loremflickr.com/320/240/restaurant,food/?random=9.83038759675332',
        viewCounts: 0,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
        CategoryId: 2,
      },
    },
    {
      id: 5,
      text: 'Ut cum fugiat alias ea asperiores sed animi.',
      UserId: 1,
      RestaurantId: 5,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      User: {
        id: 1,
        name: 'root',
        email: 'root@example.com',
        password:
          '$2a$10$/pXYqaEE24k4RAfLSItXfuXbDV4bNawnZwie9229hMzPEe/ZbDx3G',
        isAdmin: true,
        image: null,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      Restaurant: {
        id: 5,
        name: 'Idella Satterfield',
        tel: '(926) 063-2120 x581',
        address: '889 Janet Square',
        opening_hours: '08:00',
        description: 'Fuga iure quos id saepe ab itaque odit earum occaecati.',
        image:
          'https://loremflickr.com/320/240/restaurant,food/?random=36.78451119597441',
        viewCounts: 0,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
        CategoryId: 1,
      },
    },
    {
      id: 6,
      text: 'Ut laboriosam et dignissimos tempora aliquam voluptates sint.',
      UserId: 2,
      RestaurantId: 6,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      User: {
        id: 2,
        name: 'user1',
        email: 'user1@example.com',
        password:
          '$2a$10$rdYNUx3AFBhT0ACgV9rE1uplKv/1I8THZO0RGx.9kPKTi.oba7pRW',
        isAdmin: false,
        image: null,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      Restaurant: {
        id: 6,
        name: 'Angelina Quitzon I',
        tel: '811.077.2683 x24748',
        address: '1213 Nicklaus Trace',
        opening_hours: '08:00',
        description:
          'Voluptatem rem molestiae officia doloribus similique laudantium in.\nQuae ut qui non itaque minima sit cum.\nRerum eos tempore dolores eligendi totam perspiciatis ea quis.\nNihil asperiores eos distinctio non aut nisi accusantium.',
        image:
          'https://loremflickr.com/320/240/restaurant,food/?random=41.887010361261076',
        viewCounts: 0,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
        CategoryId: 1,
      },
    },
    {
      id: 7,
      text: 'Veniam culpa et minima quae natus omnis.',
      UserId: 2,
      RestaurantId: 7,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      User: {
        id: 2,
        name: 'user1',
        email: 'user1@example.com',
        password:
          '$2a$10$rdYNUx3AFBhT0ACgV9rE1uplKv/1I8THZO0RGx.9kPKTi.oba7pRW',
        isAdmin: false,
        image: null,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      Restaurant: {
        id: 7,
        name: 'Berneice Herzog',
        tel: '338-580-2426',
        address: '895 Mae Turnpike',
        opening_hours: '08:00',
        description:
          'Quod reiciendis itaque iure voluptas quo nulla provident modi aliquam.',
        image:
          'https://loremflickr.com/320/240/restaurant,food/?random=10.746556012930641',
        viewCounts: 0,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
        CategoryId: 1,
      },
    },
    {
      id: 8,
      text: 'Ut placeat error recusandae quod voluptate nobis.',
      UserId: 3,
      RestaurantId: 8,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      User: {
        id: 3,
        name: 'user2',
        email: 'user2@example.com',
        password:
          '$2a$10$JPhaLC4JdTUH08gPRSI07esdEadoY7t1e0GGytt05hqfVeQBiNJ5i',
        isAdmin: false,
        image: null,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      Restaurant: {
        id: 8,
        name: 'Zena Kuhn V',
        tel: '183.919.3331',
        address: '4856 Upton Via',
        opening_hours: '08:00',
        description: 'odio',
        image:
          'https://loremflickr.com/320/240/restaurant,food/?random=87.86589893032648',
        viewCounts: 0,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
        CategoryId: 1,
      },
    },
    {
      id: 9,
      text: 'Deleniti deleniti totam reiciendis deleniti consequatur sint dolorem perspiciatis.',
      UserId: 3,
      RestaurantId: 9,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      User: {
        id: 3,
        name: 'user2',
        email: 'user2@example.com',
        password:
          '$2a$10$JPhaLC4JdTUH08gPRSI07esdEadoY7t1e0GGytt05hqfVeQBiNJ5i',
        isAdmin: false,
        image: null,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      Restaurant: {
        id: 9,
        name: 'Florine McLaughlin DVM',
        tel: '(790) 829-4484 x00755',
        address: '39017 Mohammad Lodge',
        opening_hours: '08:00',
        description:
          'Autem eaque sed alias nisi aut facere ipsam ut laborum. Hic nostrum vero aut rerum sit cupiditate quasi. Ullam perferendis eius nisi aut. Atque ut nisi dolore eius sed soluta magni id. Aut repudiandae quos harum deserunt nemo placeat.',
        image:
          'https://loremflickr.com/320/240/restaurant,food/?random=9.756850302612353',
        viewCounts: 0,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
        CategoryId: 5,
      },
    },
    {
      id: 10,
      text: 'Assumenda similique facilis praesentium iusto officiis et et.',
      UserId: 2,
      RestaurantId: 10,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      User: {
        id: 2,
        name: 'user1',
        email: 'user1@example.com',
        password:
          '$2a$10$rdYNUx3AFBhT0ACgV9rE1uplKv/1I8THZO0RGx.9kPKTi.oba7pRW',
        isAdmin: false,
        image: null,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      Restaurant: {
        id: 10,
        name: 'Jolie Dibbert',
        tel: '962-209-3272 x73704',
        address: '354 Dare Dam',
        opening_hours: '08:00',
        description:
          'Aliquid ipsum laboriosam commodi. Veniam tempora distinctio hic expedita ipsam. Reiciendis quaerat aut exercitationem id est.\n \rNatus ipsam pariatur. Voluptate perspiciatis ipsum odio voluptas magni. Ipsa adipisci dolores quis aperiam.\n \rUt expedita aperiam dignissimos consequuntur deserunt rerum. Doloremque temporibus voluptas. Doloremque ipsam est occaecati perspiciatis facilis qui tempore et. Fugit eum illo perferendis omnis ut distinctio. Quos repudiandae libero et distinctio in tempore quae.',
        image:
          'https://loremflickr.com/320/240/restaurant,food/?random=36.11119470075997',
        viewCounts: 0,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
        CategoryId: 2,
      },
    },
  ],
};

export default {
  components: {
    NavTabs,
    NewestRestaurants,
    NewestComments,
  },
  data() {
    return {
      restaurants: [],
      comments: [],
    };
  },
  methods: {
    fetchFeeds() {
      this.restaurants = dummyData.restaurants;
      this.comments = dummyData.comments;
    },
  },
  created() {
    this.fetchFeeds();
  },
};
</script>
