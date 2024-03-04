<a name="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

  <h3 align="center">Help Me App</h3>

  <p align="center">
    A simple map that uses browser geolocation to get the phone number of the nearest selected service
    <br />
    <br />
    <a href="https://github.com/nelsonsalves/help-app/issues">Report Bug</a>
    ·
    <a href="https://github.com/nelsonsalves/help-app/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

This is a simple project where the user geolocation is used to return the phone number of the service selected by the user.
Currently two services are supported: firefighters and police. The data is stored in a pocketbase instance that can be stored locally or
as a service using providers like pockethost. The data was manually fetched from several websites to compile the database.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



### Built With

* [![Svelte][Svelte.dev]][Svelte-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started

Please follow the following instructions to install the project in your computer

### Prerequisites

This project assumes you have npm installed in your system.

### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/nelsonsalves/help-app.git
   ```
2. Install NPM packages
   ```sh
   npm install
   ```
3. Setup pocketbase instance downloading the binary from [here](https://pocketbase.io/). Extract the binary to the root of the repo and in that folder run
   ```sh
   ./pocketbase serve
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* [Pockethost](https://pockethost.io/)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/nelsonsalves/help-app.svg?style=for-the-badge
[contributors-url]: https://github.com/nelsonsalves/help-app/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/nelsonsalves/help-app.svg?style=for-the-badge
[forks-url]: https://github.com/nelsonsalves/help-app/network/members
[stars-shield]: https://img.shields.io/github/stars/nelsonsalves/help-app.svg?style=for-the-badge
[stars-url]: https://github.com/nelsonsalves/help-app/stargazers
[issues-shield]: https://img.shields.io/github/issues/nelsonsalves/help-app.svg?style=for-the-badge
[issues-url]: https://github.com/nelsonsalves/help-app/issues
[license-shield]: https://img.shields.io/github/license/nelsonsalves/help-app.svg?style=for-the-badge
[license-url]: https://github.com/nelsonsalves/help-app/blob/master/LICENSE.txt
[Svelte.dev]: https://img.shields.io/badge/Svelte-4A4A55?style=for-the-badge&logo=svelte&logoColor=FF3E00
[Svelte-url]: https://svelte.dev/