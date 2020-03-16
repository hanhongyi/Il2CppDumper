# Il2CppDumper
Better version of https://github.com/Jumboperson/PokemonGoDumper

	
	// Someone asked me about these two constants so I thought I should document what they are.
	// These two pointers are the first two arguments passed to il2cpp::vm::MetadataCache::Register in the libil2cpp.so binary.
	// Updating them manually should be fairly trivial, just find where il2cpp::vm::MetadataCache::Register is called and use the first two args for \
	  code and metadata respectively.
    
    // Steps: 
    // 1.Use IDA to find out exported function 'il2cpp_custom_attrs_has_attr', then you can simply get 'MetadataCache::HasAttribute'
    // 2.From 'MetadataCache::HasAttribute' get 'MetadataCache::GetTypeInfoFromTypeIndex', then use "jump to xref" to any global item which used in this function
    // 3.Finally you may get function 'MetadataCache::GetTypeInfoFromTypeIndex', which content all global variant you need.
    // 4.Make sure 'MetadataCache::Initialize' is using string "global-metadata.dat" in first line.
