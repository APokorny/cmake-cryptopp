project(cryptopp VERSION 1.0.0 LANGUAGES CXX)
add_library(cryptopp STATIC
    cryptopp/3way.cpp
    cryptopp/adler32.cpp
    cryptopp/algebra.cpp
    cryptopp/algparam.cpp
    cryptopp/arc4.cpp
    cryptopp/aria.cpp
    cryptopp/aria_simd.cpp
    cryptopp/ariatab.cpp
    cryptopp/asn.cpp
    cryptopp/authenc.cpp
    cryptopp/base32.cpp
    cryptopp/base64.cpp
    cryptopp/basecode.cpp
    cryptopp/bfinit.cpp
    cryptopp/blake2b_simd.cpp
    cryptopp/blake2.cpp
    cryptopp/blake2s_simd.cpp
    cryptopp/blowfish.cpp
    cryptopp/blumshub.cpp
    cryptopp/camellia.cpp
    cryptopp/cast.cpp
    cryptopp/casts.cpp
    cryptopp/cbcmac.cpp
    cryptopp/ccm.cpp
    #cryptopp/chacha_avx.cpp
    cryptopp/chacha.cpp
    cryptopp/chacha_simd.cpp
    cryptopp/cham.cpp
    cryptopp/cham_simd.cpp
    cryptopp/channels.cpp
    cryptopp/cmac.cpp
    cryptopp/cpu.cpp
    cryptopp/crc.cpp
    cryptopp/crc_simd.cpp
    cryptopp/cryptlib.cpp
    cryptopp/darn.cpp
    cryptopp/default.cpp
    cryptopp/des.cpp
    cryptopp/dessp.cpp
    cryptopp/dh2.cpp
    cryptopp/dh.cpp
    cryptopp/donna_32.cpp
    cryptopp/donna_64.cpp
    cryptopp/donna_sse.cpp
    cryptopp/dsa.cpp
    cryptopp/eax.cpp
    cryptopp/ecp.cpp
    cryptopp/elgamal.cpp
    cryptopp/emsa2.cpp
    cryptopp/esign.cpp
    cryptopp/files.cpp
    cryptopp/filters.cpp
    cryptopp/fips140.cpp
    cryptopp/fipsalgt.cpp
    cryptopp/gcm.cpp
    cryptopp/gcm_simd.cpp
    cryptopp/gf2_32.cpp
    cryptopp/gf256.cpp
    cryptopp/gf2n.cpp
    cryptopp/gf2n_simd.cpp
    cryptopp/gfpcrypt.cpp
    cryptopp/gost.cpp
    cryptopp/gzip.cpp
    cryptopp/hc128.cpp
    cryptopp/hc256.cpp
    cryptopp/hex.cpp
    cryptopp/hight.cpp
    cryptopp/hmac.cpp
    cryptopp/hrtimer.cpp
    cryptopp/ida.cpp
    cryptopp/idea.cpp
    cryptopp/integer.cpp
    cryptopp/iterhash.cpp
    cryptopp/kalyna.cpp
    cryptopp/kalynatab.cpp
    cryptopp/keccakc.cpp
    cryptopp/keccak.cpp
    cryptopp/lea.cpp
    cryptopp/lea_simd.cpp
    cryptopp/luc.cpp
    cryptopp/mars.cpp
    cryptopp/marss.cpp
    cryptopp/md2.cpp
    cryptopp/md4.cpp
    cryptopp/md5.cpp
    cryptopp/misc.cpp
    cryptopp/modes.cpp
    cryptopp/mqueue.cpp
    cryptopp/mqv.cpp
    cryptopp/nbtheory.cpp
    cryptopp/neon_simd.cpp
    cryptopp/oaep.cpp
    cryptopp/osrng.cpp
    cryptopp/padlkrng.cpp
    cryptopp/panama.cpp
    cryptopp/pch.cpp
    cryptopp/pkcspad.cpp
    cryptopp/poly1305.cpp
    cryptopp/polynomi.cpp
    #cryptopp/ppc_power7.cpp
    #cryptopp/ppc_power8.cpp
    #cryptopp/ppc_power9.cpp
    #cryptopp/ppc_simd.cpp
    cryptopp/pssr.cpp
    cryptopp/pubkey.cpp
    cryptopp/queue.cpp
    cryptopp/rabbit.cpp
    cryptopp/rabin.cpp
    cryptopp/randpool.cpp
    cryptopp/rc2.cpp
    cryptopp/rc5.cpp
    cryptopp/rc6.cpp
    cryptopp/rdrand.cpp
    cryptopp/rdtables.cpp
    cryptopp/rijndael.cpp
    cryptopp/rijndael_simd.cpp
    cryptopp/ripemd.cpp
    cryptopp/rng.cpp
    cryptopp/rsa.cpp
    cryptopp/rw.cpp
    cryptopp/safer.cpp
    cryptopp/salsa.cpp
    cryptopp/scrypt.cpp
    cryptopp/seal.cpp
    cryptopp/seed.cpp
    cryptopp/serpent.cpp
    cryptopp/sha3.cpp
    cryptopp/shacal2.cpp
    cryptopp/shacal2_simd.cpp
    cryptopp/sha.cpp
    cryptopp/sharkbox.cpp
    cryptopp/shark.cpp
    cryptopp/sha_simd.cpp
    cryptopp/simeck.cpp
    cryptopp/simeck_simd.cpp
    cryptopp/simon128_simd.cpp
    cryptopp/simon64_simd.cpp
    cryptopp/simon.cpp
    cryptopp/simple.cpp
    cryptopp/skipjack.cpp
    cryptopp/sm3.cpp
    cryptopp/sm4.cpp
    cryptopp/sm4_simd.cpp
    cryptopp/sosemanuk.cpp
    cryptopp/speck128_simd.cpp
    cryptopp/speck64_simd.cpp
    cryptopp/speck.cpp
    cryptopp/square.cpp
    cryptopp/squaretb.cpp
    cryptopp/sse_simd.cpp
    cryptopp/tea.cpp
    cryptopp/tftables.cpp
    cryptopp/threefish.cpp
    cryptopp/tiger.cpp
    cryptopp/tigertab.cpp
    cryptopp/ttmac.cpp
    cryptopp/tweetnacl.cpp
    cryptopp/twofish.cpp
    cryptopp/vmac.cpp
    cryptopp/wake.cpp
    cryptopp/whrlpool.cpp
    cryptopp/xed25519.cpp
    cryptopp/xtr.cpp
    cryptopp/xtrcrypt.cpp
    cryptopp/zdeflate.cpp
    cryptopp/zinflate.cpp
    cryptopp/zlib.cpp)

if(USE_EXPORTED_TEMPLATES)
    target_sources(cryptopp PRIVATE
        cryptopp/eprecomp.cpp
        cryptopp/ec2n.cpp
        cryptopp/eccrypto.cpp
        cryptopp/strciphr.cpp
        )
endif()

target_compile_options(cryptopp PUBLIC -DCRYPTOPP_MANUALLY_INSTANTIATE_TEMPLATES)
if(NOT CMAKE_SYSTEM_NAME MATCHES "Emscripten" AND CMAKE_CXX_COMPILER_ID MATCHES "GNU")
    target_compile_options(cryptopp PRIVATE -mssse3 -msse4.1 -msse4.2 -msse2 -mpclmul -maes -msha)
endif()


add_library(CryptoPP::cryptopp ALIAS cryptopp)

target_include_directories(cryptopp PUBLIC $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}> $<INSTALL_INTERFACE:include>)
install(TARGETS cryptopp EXPORT cryptopp-Targets
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
    RUNTIME DESTINATION bin
    INCLUDES DESTINATION include)
install(EXPORT cryptopp-Targets
    FILE cryptopp-Targets.cmake
    NAMESPACE CryptoPP::
    DESTINATION lib/cmake/CryptoPP)
