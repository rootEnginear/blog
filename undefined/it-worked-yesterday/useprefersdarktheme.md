# usePrefersDarkTheme

```text
import { useState, useEffect } from 'react';

export const usePrefersDarkTheme = () => {
  const [prefersDarkTheme, setPrefersDarkTheme] = useState(false);

  useEffect(() => {
    if (!window.matchMedia) return;
    const isDarkMode = window.matchMedia('(prefers-color-scheme: dark)');

    const updatePreferDarkTheme = () => {
      setPrefersDarkTheme(isDarkMode.matches);
    };

    updatePreferDarkTheme();
    isDarkMode.addEventListener('change', updatePreferDarkTheme);

    return () => {
      isDarkMode.removeEventListener('change', updatePreferDarkTheme);
    };
  }, []);

  return {
    prefersDarkTheme
  };
};

```

