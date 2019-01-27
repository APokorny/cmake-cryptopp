CMake integratiion for Crypto++
-------------------------------

This creates a cmake target and cmake configuration in namespace CryptoPP.

  add_subdirectory(crypto++)
   
  target_link_libraries(MyExec PRIVATE CryptoPP)
