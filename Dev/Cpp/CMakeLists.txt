# Debug Release�Ɍ���
set(CMAKE_CONFIGURATION_TYPES Debug Release CACHE TYPE INTERNAL FORCE )

# �v���W�F�N�g��
project(Effekseer)

# CMake �o�[�W�����`�F�b�N
cmake_minimum_required(VERSION 2.8)

# MSVC�����ݒ�
if (MSVC)
	option(USE_MSVC_RUNTIME_LIBRARY_DLL "Use MSVC runtime library DLL" OFF)
	option(USE_DIRECTXTEX "Use DirectXTex" OFF)
endif()

option(USE_INTERNAL_LOADER "Use Internal Loader" ON)

option(USE_GLEW_STATIC "Use Glew static library" ON)
option(USE_GLEW_DLL "Use Glew DLL" OFF)
option(USE_OPENGLES2 "Use OpenGL ES2" OFF)

# �\�[�X�R�[�h�ݒ�
set(effekseer_src
	Effekseer/Effekseer/Effekseer.Client.cpp
	Effekseer/Effekseer/Effekseer.Color.cpp
	Effekseer/Effekseer/Effekseer.CriticalSection.cpp
	Effekseer/Effekseer/Effekseer.DefaultEffectLoader.cpp
	Effekseer/Effekseer/Effekseer.DefaultFile.cpp
	Effekseer/Effekseer/Effekseer.Effect.cpp
	Effekseer/Effekseer/Effekseer.EffectNode.cpp
	Effekseer/Effekseer/Effekseer.EffectNodeModel.cpp
	Effekseer/Effekseer/Effekseer.EffectNodeRibbon.cpp
	Effekseer/Effekseer/Effekseer.EffectNodeRing.cpp
	Effekseer/Effekseer/Effekseer.EffectNodeRoot.cpp
	Effekseer/Effekseer/Effekseer.EffectNodeSprite.cpp
	Effekseer/Effekseer/Effekseer.EffectNodeTrack.cpp
	Effekseer/Effekseer/Effekseer.FCurves.cpp
	Effekseer/Effekseer/Effekseer.Instance.cpp
	Effekseer/Effekseer/Effekseer.InstanceContainer.cpp
	Effekseer/Effekseer/Effekseer.InstanceGlobal.cpp
	Effekseer/Effekseer/Effekseer.InstanceGroup.cpp
	Effekseer/Effekseer/Effekseer.Manager.cpp
	Effekseer/Effekseer/Effekseer.Matrix43.cpp
	Effekseer/Effekseer/Effekseer.Matrix44.cpp
	Effekseer/Effekseer/Effekseer.RectF.cpp
	Effekseer/Effekseer/Effekseer.Setting.cpp
	Effekseer/Effekseer/Effekseer.Server.cpp
	Effekseer/Effekseer/Effekseer.Socket.cpp
	Effekseer/Effekseer/Effekseer.Thread.cpp
	Effekseer/Effekseer/Effekseer.Vector2D.cpp
	Effekseer/Effekseer/Effekseer.Vector3D.cpp)


set(effekseer_renderer_common_src
	EffekseerRendererCommon/EffekseerRenderer.IndexBufferBase.cpp
	EffekseerRendererCommon/EffekseerRenderer.ModelRendererBase.cpp
	EffekseerRendererCommon/EffekseerRenderer.RenderStateBase.cpp
	EffekseerRendererCommon/EffekseerRenderer.Renderer.cpp
	EffekseerRendererCommon/EffekseerRenderer.RibbonRendererBase.cpp
	EffekseerRendererCommon/EffekseerRenderer.RingRendererBase.cpp
	EffekseerRendererCommon/EffekseerRenderer.SpriteRendererBase.cpp
	EffekseerRendererCommon/EffekseerRenderer.TrackRendererBase.cpp
	EffekseerRendererCommon/EffekseerRenderer.VertexBufferBase.cpp)

set(effekseer_renderer_dx9_src
	EffekseerRendererDX9/EffekseerRenderer/EffekseerRendererDX9.DeviceObject.cpp
	EffekseerRendererDX9/EffekseerRenderer/EffekseerRendererDX9.IndexBuffer.cpp
	EffekseerRendererDX9/EffekseerRenderer/EffekseerRendererDX9.ModelLoader.cpp
	EffekseerRendererDX9/EffekseerRenderer/EffekseerRendererDX9.ModelRenderer.cpp
	EffekseerRendererDX9/EffekseerRenderer/EffekseerRendererDX9.Renderer.cpp
	EffekseerRendererDX9/EffekseerRenderer/EffekseerRendererDX9.RenderState.cpp
	EffekseerRendererDX9/EffekseerRenderer/EffekseerRendererDX9.RibbonRenderer.cpp
	EffekseerRendererDX9/EffekseerRenderer/EffekseerRendererDX9.RingRenderer.cpp
	EffekseerRendererDX9/EffekseerRenderer/EffekseerRendererDX9.Shader.cpp
	EffekseerRendererDX9/EffekseerRenderer/EffekseerRendererDX9.SpriteRenderer.cpp
	EffekseerRendererDX9/EffekseerRenderer/EffekseerRendererDX9.TextureLoader.cpp
	EffekseerRendererDX9/EffekseerRenderer/EffekseerRendererDX9.TrackRenderer.cpp
	EffekseerRendererDX9/EffekseerRenderer/EffekseerRendererDX9.VertexBuffer.cpp)

set(effekseer_renderer_dx11_src
	EffekseerRendererDX11/EffekseerRenderer/EffekseerRendererDX11.DeviceObject.cpp
	EffekseerRendererDX11/EffekseerRenderer/EffekseerRendererDX11.IndexBuffer.cpp
	EffekseerRendererDX11/EffekseerRenderer/EffekseerRendererDX11.ModelLoader.cpp
	EffekseerRendererDX11/EffekseerRenderer/EffekseerRendererDX11.ModelRenderer.cpp
	EffekseerRendererDX11/EffekseerRenderer/EffekseerRendererDX11.Renderer.cpp
	EffekseerRendererDX11/EffekseerRenderer/EffekseerRendererDX11.RenderState.cpp
	EffekseerRendererDX11/EffekseerRenderer/EffekseerRendererDX11.RibbonRenderer.cpp
	EffekseerRendererDX11/EffekseerRenderer/EffekseerRendererDX11.RingRenderer.cpp
	EffekseerRendererDX11/EffekseerRenderer/EffekseerRendererDX11.Shader.cpp
	EffekseerRendererDX11/EffekseerRenderer/EffekseerRendererDX11.SpriteRenderer.cpp
	EffekseerRendererDX11/EffekseerRenderer/EffekseerRendererDX11.TextureLoader.cpp
	EffekseerRendererDX11/EffekseerRenderer/EffekseerRendererDX11.TrackRenderer.cpp
	EffekseerRendererDX11/EffekseerRenderer/EffekseerRendererDX11.VertexBuffer.cpp)

set(effekseer_renderer_gl_src
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.DeviceObject.cpp
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.GLExtension.cpp
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.IndexBuffer.cpp
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.ModelLoader.cpp
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.ModelRenderer.cpp
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.Renderer.cpp
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.RenderState.cpp
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.RibbonRenderer.cpp
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.RingRenderer.cpp
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.Shader.cpp
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.SpriteRenderer.cpp
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.TextureLoader.cpp
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.TrackRenderer.cpp
	EffekseerRendererGL/EffekseerRenderer/EffekseerRendererGL.VertexBuffer.cpp)

list(APPEND effekseer_renderer_dx9_src
	${effekseer_renderer_common_src})

list(APPEND effekseer_renderer_dx11_src
	${effekseer_renderer_common_src})

list(APPEND effekseer_renderer_gl_src
	${effekseer_renderer_common_src})

# �C���N���[�h�̐ݒ�
include_directories(
	Effekseer/
	)

# �R���p�C�����ǉ�
add_library( effekseer STATIC ${effekseer_src} )

if (MSVC)
add_library( effekseer_renderer_dx9 STATIC ${effekseer_renderer_dx9_src} )
add_library( effekseer_renderer_dx11 STATIC ${effekseer_renderer_dx11_src} )
endif()

add_library( effekseer_renderer_gl STATIC ${effekseer_renderer_gl_src} )

# �t���O����
if (MSVC)
	if (NOT USE_MSVC_RUNTIME_LIBRARY_DLL)
		foreach (flag CMAKE_C_FLAGS
			CMAKE_C_FLAGS_DEBUG
			CMAKE_C_FLAGS_RELEASE
			CMAKE_CXX_FLAGS
			CMAKE_CXX_FLAGS_DEBUG
			CMAKE_CXX_FLAGS_RELEASE)

			if (${flag} MATCHES "/MD")
				string(REGEX REPLACE "/MD" "/MT" ${flag} "${${flag}}")
			endif()
			if (${flag} MATCHES "/MDd")
				string(REGEX REPLACE "/MDd" "/MTd" ${flag} "${${flag}}")
			endif()
		endforeach()
	endif()
endif()

if (USE_INTERNAL_LOADER)
	add_definitions(-D__EFFEKSEER_RENDERER_INTERNAL_LOADER__)
endif()

if (USE_GLEW_STATIC)
	add_definitions(-D__EFFEKSEER_RENDERER_GL_GLEW_S__)
endif()

if (USE_GLEW_DLL)
	add_definitions(-D__EFFEKSEER_RENDERER_GL_GLEW__)
endif()

if (USE_OPENGLES2)
	add_definitions(-D__EFFEKSEER_RENDERER_GLES2__)
endif()

if (MSVC)
if (USE_DIRECTXTEX)
	add_definitions(-D__EFFEKSEER_RENDERER_DIRECTXTEX)
	add_definitions(-D__EFFEKSEER_RENDERER_DIRECTXTEX__)
endif()
endif()


# �o�͐�̐ݒ�
if (MSVC)
set_target_properties(effekseer PROPERTIES OUTPUT_NAME_DEBUG "Effekseer" )
set_target_properties(effekseer PROPERTIES OUTPUT_NAME_RELEASE "Effekseer" )
else()
set_target_properties(effekseer PROPERTIES OUTPUT_NAME "Effekseer" )
endif()

if (MSVC)
if (MSVC)
set_target_properties(effekseer_renderer_dx9 PROPERTIES OUTPUT_NAME_DEBUG "EffekseerRendererDX9" )
set_target_properties(effekseer_renderer_dx9 PROPERTIES OUTPUT_NAME_RELEASE "EffekseerRendererDX9" )
else()
set_target_properties(effekseer_renderer_dx9 PROPERTIES OUTPUT_NAME "EffekseerRendererDX9" )
endif()
endif()

if (MSVC)
if (MSVC)
set_target_properties(effekseer_renderer_dx11 PROPERTIES OUTPUT_NAME_DEBUG "EffekseerRendererDX11" )
set_target_properties(effekseer_renderer_dx11 PROPERTIES OUTPUT_NAME_RELEASE "EffekseerRendererDX11" )
else()
set_target_properties(effekseer_renderer_dx11 PROPERTIES OUTPUT_NAME "EffekseerRendererDX11" )
endif()
endif()

if (MSVC)
set_target_properties(effekseer_renderer_gl PROPERTIES OUTPUT_NAME_DEBUG "EffekseerRendererGL" )
set_target_properties(effekseer_renderer_gl PROPERTIES OUTPUT_NAME_RELEASE "EffekseerRendererGL" )
else()
set_target_properties(effekseer_renderer_gl PROPERTIES OUTPUT_NAME "EffekseerRendererGL" )
endif()


install(
	TARGETS effekseer
	ARCHIVE DESTINATION lib
	LIBRARY DESTINATION lib)

if (MSVC)
install(
	TARGETS effekseer_renderer_dx9
	ARCHIVE DESTINATION lib
	LIBRARY DESTINATION lib)
endif()

if (MSVC)
install(
	TARGETS effekseer_renderer_dx11
	ARCHIVE DESTINATION lib
	LIBRARY DESTINATION lib)
endif()

install(
	TARGETS effekseer_renderer_gl
	ARCHIVE DESTINATION lib
	LIBRARY DESTINATION lib)