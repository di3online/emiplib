apply_include_paths("${EMIPLIB_INTERNAL_INCLUDES}")
apply_include_paths("${EMIPLIB_EXTERNAL_INCLUDES}")

foreach(IDX avsession feedbackexample oscfeedbackexample multiplesoundfileplayer simplechain soundfileplayer soundrecorder pushtotalk
	    pushtotalk2)
	add_executable(${IDX} ${IDX}.cpp)
	if (UNIX OR EMIPLIB_COMPILE_STATIC)
		target_link_libraries(${IDX} emiplib-static ${EMIPLIB_LINK_LIBS})
	else ()
		target_link_libraries(${IDX} emiplib-shared ${EMIPLIB_LINK_LIBS})
	endif (UNIX OR EMIPLIB_COMPILE_STATIC)
endforeach(IDX)

