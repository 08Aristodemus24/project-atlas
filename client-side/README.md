# Insights:
1. By default, SvelteKit will render your components on the server. The components will be rendered in the browser using hydration on subsequent requests. That means that at some point in the component lifecycle, particular browser-specific objects like  document document  will not be available .
