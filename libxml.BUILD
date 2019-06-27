genrule(
    name = "gen_configure",
    srcs = [
        "Makefile.in",
        "config.guess",
        "config.h.in",
        "config.sub",
        "configure",
        "entities.c",
        "install-sh",
        "libxml-2.0.pc.in",
        "libxml-2.0-uninstalled.pc.in",
        "libxml2-config.cmake.in",
        "libxml.spec.in",
        "ltmain.sh",
        "missing",
        "xml2-config.in",
        "doc/Makefile.in",
        "doc/devhelp/Makefile.in",
        "doc/examples/Makefile.in",
        "example/Makefile.in",
        "include/Makefile.in",
        "include/libxml/Makefile.in",
        "include/libxml/xmlversion.h.in",
        "python/Makefile.in",
        "python/setup.py.in",
        "python/tests/Makefile.in",
        "xstc/Makefile.in",
    ],
    outs = [
        "config.h",
        "include/libxml/xmlversion.h",
    ],
    cmd = "./$(location configure) --silent --without-lzma --without-iconv " +
          "&& cp --verbose -- config.h $(location config.h) " +
          "&& cp --verbose -- include/libxml/xmlversion.h $(location include/libxml/xmlversion.h)",
)

cc_library(
    name = "libxml",
    srcs = [
        "HTMLparser.c",
        "HTMLtree.c",
        "SAX.c",
        "SAX2.c",
        "buf.c",
        "c14n.c",
        "catalog.c",
        "chvalid.c",
        "debugXML.c",
        "dict.c",
        "encoding.c",
        "entities.c",
        "error.c",
        "globals.c",
        "hash.c",
        "legacy.c",
        "list.c",
        "nanoftp.c",
        "nanohttp.c",
        "parser.c",
        "parserInternals.c",
        "pattern.c",
        "relaxng.c",
        "schematron.c",
        "threads.c",
        "tree.c",
        "uri.c",
        "valid.c",
        "xinclude.c",
        "xlink.c",
        "xmlIO.c",
        "xmlmemory.c",
        "xmlmodule.c",
        "xmlreader.c",
        "xmlregexp.c",
        "xmlsave.c",
        "xmlschemas.c",
        "xmlschemastypes.c",
        "xmlstring.c",
        "xmlunicode.c",
        "xmlwriter.c",
        "xpath.c",
        "xpointer.c",
        "xzlib.c",
    ],
    hdrs = [
        "config.h",
        "include/libxml/xmlversion.h",
    ] + glob(
        [
            "*.h",
            "include/libxml/*.h",
        ],
        exclude = [
            # Exclude the pre-made version that ships with the tarball,
            # use the genrule output from ./configure instead.
            "include/libxml/xmlversion.h",
        ],
    ),
    copts = [
        "-D_REENTRANT",
        "-DHAVE_CONFIG_H",
        "-w",
    ],
    includes = [
        ".",
        "include",
    ],
    linkopts = ["-pthread"],
    textual_hdrs = ["trionan.c"],
    visibility = ["//visibility:public"],
)