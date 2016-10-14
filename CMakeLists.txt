cmake_minimum_required ( VERSION 2.6 )

set ( TARGET_NAME live666 )

project ( ${TARGET_NAME} )

set ( ${TARGET_NAME}_VERSION_MAJOR "2016" )
set ( ${TARGET_NAME}_VERSION_MINOR "05" )
set ( ${TARGET_NAME}_VERSION_PATCH "20" )
set ( ${TARGET_NAME}_VERSION "${${TARGET_NAME}_VERSION_MAJOR}.${${TARGET_NAME}_VERSION_MINOR}.${${TARGET_NAME}_VERSION_PATCH}" )

if ( CMAKE_COMPILER_IS_GNUCXX )
   set ( CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS} "-fpermissive" )
endif ()

set ( BUILD_SHARED_LIBS TRUE )

set ( ${TARGET_NAME}_HOME ${CMAKE_CURRENT_SOURCE_DIR} )
include_directories ( ${${TARGET_NAME}_HOME}/UsageEnvironment/include )
include_directories ( ${${TARGET_NAME}_HOME}/BasicUsageEnvironment/include )
include_directories ( ${${TARGET_NAME}_HOME}/groupsock/include )
include_directories ( ${${TARGET_NAME}_HOME}/liveMedia/include )

if ( WIN32 )
   set ( ${TARGET_NAME}_DEFINITIONS -DWINNT )
else ()
   set ( ${TARGET_NAME}_DEFINITIONS "" )
endif ()

list ( APPEND ${TARGET_NAME}_DEFINITIONS
   -D${TARGET_NAME}_EXPORTS
)
add_definitions ( ${${TARGET_NAME}_DEFINITIONS} )


list ( APPEND ${TARGET_NAME}_HEADERS_USAGEENVIRONMENT
   ${${TARGET_NAME}_HOME}/UsageEnvironment/include/Boolean.hh
   ${${TARGET_NAME}_HOME}/UsageEnvironment/include/HashTable.hh
   ${${TARGET_NAME}_HOME}/UsageEnvironment/include/strDup.hh
   ${${TARGET_NAME}_HOME}/UsageEnvironment/include/UsageEnvironment.hh
   ${${TARGET_NAME}_HOME}/UsageEnvironment/include/UsageEnvironment_version.hh
)
# Group (Filter) source files
source_group ( "Header Files\\UsageEnvironment" FILES ${${TARGET_NAME}_HEADERS_USAGEENVIRONMENT} )

list ( APPEND ${TARGET_NAME}_HEADERS_BASICUSAGEENVIRONMENT
   ${${TARGET_NAME}_HOME}/BasicUsageEnvironment/include/BasicHashTable.hh
   ${${TARGET_NAME}_HOME}/BasicUsageEnvironment/include/BasicUsageEnvironment.hh
   ${${TARGET_NAME}_HOME}/BasicUsageEnvironment/include/BasicUsageEnvironment_version.hh
   ${${TARGET_NAME}_HOME}/BasicUsageEnvironment/include/BasicUsageEnvironment0.hh
   ${${TARGET_NAME}_HOME}/BasicUsageEnvironment/include/DelayQueue.hh
   ${${TARGET_NAME}_HOME}/BasicUsageEnvironment/include/HandlerSet.hh
)
# Group (Filter) source files
source_group ( "Header Files\\BasicUsageEnvironment" FILES ${${TARGET_NAME}_HEADERS_BASICUSAGEENVIRONMENT} )

list ( APPEND ${TARGET_NAME}_HEADERS_GROUPSOCK
   ${${TARGET_NAME}_HOME}/groupsock/include/GroupEId.hh
   ${${TARGET_NAME}_HOME}/groupsock/include/Groupsock.hh
   ${${TARGET_NAME}_HOME}/groupsock/include/groupsock_version.hh
   ${${TARGET_NAME}_HOME}/groupsock/include/GroupsockHelper.hh
   ${${TARGET_NAME}_HOME}/groupsock/include/IOHandlers.hh
   ${${TARGET_NAME}_HOME}/groupsock/include/NetAddress.hh
   ${${TARGET_NAME}_HOME}/groupsock/include/NetCommon.h
   ${${TARGET_NAME}_HOME}/groupsock/include/NetInterface.hh
   ${${TARGET_NAME}_HOME}/groupsock/include/TunnelEncaps.hh
)
# Group (Filter) source files
source_group ( "Header Files\\groupsock" FILES ${${TARGET_NAME}_HEADERS_GROUPSOCK} )

list ( APPEND ${TARGET_NAME}_HEADERS_LIVEMEDIA
   ${${TARGET_NAME}_HOME}/liveMedia/include/AC3AudioFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/AC3AudioRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/AC3AudioRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/AC3AudioStreamFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/ADTSAudioFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/ADTSAudioFileSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/AMRAudioFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/AMRAudioFileSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/AMRAudioFileSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/AMRAudioRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/AMRAudioRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/AMRAudioSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/AudioInputDevice.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/AudioRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/AVIFileSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/Base64.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/BasicUDPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/BasicUDPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/BitVector.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/ByteStreamFileSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/ByteStreamMemoryBufferSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/ByteStreamMultiFileSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/DeviceSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/DigestAuthentication.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/DVVideoFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/DVVideoRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/DVVideoRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/DVVideoStreamFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/FileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/FileSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/FramedFileSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/FramedFilter.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/FramedSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/GenericMediaServer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/GSMAudioRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H261VideoRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H263plusVideoFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H263plusVideoRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H263plusVideoRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H263plusVideoStreamFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H264or5VideoFileSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H264or5VideoRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H264or5VideoStreamDiscreteFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H264or5VideoStreamFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H264VideoFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H264VideoFileSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H264VideoRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H264VideoRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H264VideoStreamDiscreteFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H264VideoStreamFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H265VideoFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H265VideoFileSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H265VideoRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H265VideoRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H265VideoStreamDiscreteFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/H265VideoStreamFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/InputFile.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/JPEGVideoRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/JPEGVideoRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/JPEGVideoSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/liveMedia.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/liveMedia_version.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/Locale.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MatroskaFile.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MatroskaFileServerDemux.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/Media.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MediaSession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MediaSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MediaSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MediaTranscodingTable.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MP3ADU.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MP3ADUinterleaving.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MP3ADURTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MP3ADURTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MP3ADUTranscoder.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MP3AudioFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MP3FileSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MP3Transcoder.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG1or2AudioRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG1or2AudioRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG1or2AudioStreamFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG1or2Demux.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG1or2DemuxedElementaryStream.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG1or2DemuxedServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG1or2FileServerDemux.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG1or2VideoFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG1or2VideoRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG1or2VideoRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG1or2VideoStreamDiscreteFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG1or2VideoStreamFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG2IndexFromTransportStream.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG2TransportFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG2TransportStreamFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG2TransportStreamFromESSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG2TransportStreamFromPESSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG2TransportStreamIndexFile.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG2TransportStreamMultiplexor.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG2TransportStreamTrickModeFilter.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG2TransportUDPServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG4ESVideoRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG4ESVideoRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG4GenericRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG4GenericRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG4LATMAudioRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG4LATMAudioRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG4VideoFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG4VideoStreamDiscreteFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEG4VideoStreamFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MPEGVideoStreamFramer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MultiFramedRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/MultiFramedRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/OggFile.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/OggFileServerDemux.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/OggFileSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/OnDemandServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/ourMD5.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/OutputFile.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/PassiveServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/ProxyServerMediaSession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/QCELPAudioRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/QuickTimeFileSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/QuickTimeGenericRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/RTCP.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/RTPInterface.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/RTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/RTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/RTSPClient.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/RTSPCommon.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/RTSPRegisterSender.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/RTSPServer.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/RTSPServerSupportingHTTPStreaming.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/ServerMediaSession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/SimpleRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/SimpleRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/SIPClient.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/StreamReplicator.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/T140TextRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/TCPStreamSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/TextRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/TheoraVideoRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/TheoraVideoRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/uLawAudioFilter.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/VideoRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/VorbisAudioRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/VorbisAudioRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/VP8VideoRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/VP8VideoRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/VP9VideoRTPSink.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/VP9VideoRTPSource.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/WAVAudioFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/include/WAVAudioFileSource.hh
)
# Group (Filter) source files
source_group ( "Header Files\\liveMedia" FILES ${${TARGET_NAME}_HEADERS_LIVEMEDIA} )

list ( APPEND ${TARGET_NAME}_HEADERS
   ${${TARGET_NAME}_HEADERS_USAGEENVIRONMENT}
   ${${TARGET_NAME}_HEADERS_BASICUSAGEENVIRONMENT}
   ${${TARGET_NAME}_HEADERS_GROUPSOCK}
   ${${TARGET_NAME}_HEADERS_LIVEMEDIA}
)


# C/C++-Sources
list ( APPEND ${TARGET_NAME}_SOURCES_USAGEENVIRONMENT
   ${${TARGET_NAME}_HOME}/UsageEnvironment/HashTable.cpp
   ${${TARGET_NAME}_HOME}/UsageEnvironment/strDup.cpp
   ${${TARGET_NAME}_HOME}/UsageEnvironment/UsageEnvironment.cpp
)
# Group (Filter) source files
source_group ( "Source Files\\UsageEnvironment" FILES ${${TARGET_NAME}_SOURCES_USAGEENVIRONMENT} )

# C/C++-Sources
list ( APPEND ${TARGET_NAME}_SOURCES_BASICUSAGEENVIRONMENT
   ${${TARGET_NAME}_HOME}/BasicUsageEnvironment/BasicHashTable.cpp
   ${${TARGET_NAME}_HOME}/BasicUsageEnvironment/BasicTaskScheduler.cpp
   ${${TARGET_NAME}_HOME}/BasicUsageEnvironment/BasicTaskScheduler0.cpp
   ${${TARGET_NAME}_HOME}/BasicUsageEnvironment/BasicUsageEnvironment.cpp
   ${${TARGET_NAME}_HOME}/BasicUsageEnvironment/BasicUsageEnvironment0.cpp
   ${${TARGET_NAME}_HOME}/BasicUsageEnvironment/DelayQueue.cpp
)
# Group (Filter) source files
source_group ( "Source Files\\BasicUsageEnvironment" FILES ${${TARGET_NAME}_SOURCES_BASICUSAGEENVIRONMENT} )

# C/C++-Sources
list ( APPEND ${TARGET_NAME}_SOURCES_GROUPSOCK
   ${${TARGET_NAME}_HOME}/groupsock/GroupEId.cpp
   ${${TARGET_NAME}_HOME}/groupsock/Groupsock.cpp
   ${${TARGET_NAME}_HOME}/groupsock/GroupsockHelper.cpp
   ${${TARGET_NAME}_HOME}/groupsock/inet.c
   ${${TARGET_NAME}_HOME}/groupsock/IOHandlers.cpp
   ${${TARGET_NAME}_HOME}/groupsock/NetAddress.cpp
   ${${TARGET_NAME}_HOME}/groupsock/NetInterface.cpp
)
# Group (Filter) source files
source_group ( "Source Files\\groupsock" FILES ${${TARGET_NAME}_SOURCES_GROUPSOCK} )

# C/C++-Sources
list ( APPEND ${TARGET_NAME}_SOURCES_LIVEMEDIA
   ${${TARGET_NAME}_HOME}/liveMedia/AC3AudioFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/AC3AudioRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/AC3AudioRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/AC3AudioStreamFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/ADTSAudioFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/ADTSAudioFileSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/AMRAudioFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/AMRAudioFileSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/AMRAudioFileSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/AMRAudioRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/AMRAudioRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/AMRAudioSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/AudioInputDevice.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/AudioRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/AVIFileSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/Base64.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/BasicUDPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/BasicUDPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/BitVector.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/ByteStreamFileSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/ByteStreamMemoryBufferSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/ByteStreamMultiFileSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/DeviceSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/DigestAuthentication.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/DVVideoFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/DVVideoRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/DVVideoRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/DVVideoStreamFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/EBMLNumber.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/EBMLNumber.hh
   ${${TARGET_NAME}_HOME}/liveMedia/FileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/FileSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/FramedFileSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/FramedFilter.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/FramedSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/GenericMediaServer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/GSMAudioRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H261VideoRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H263plusVideoFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H263plusVideoRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H263plusVideoRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H263plusVideoStreamFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H263plusVideoStreamParser.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H263plusVideoStreamParser.hh
   ${${TARGET_NAME}_HOME}/liveMedia/H264or5VideoFileSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H264or5VideoRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H264or5VideoStreamDiscreteFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H264or5VideoStreamFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H264VideoFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H264VideoFileSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H264VideoRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H264VideoRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H264VideoStreamDiscreteFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H264VideoStreamFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H265VideoFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H265VideoFileSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H265VideoRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H265VideoRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H265VideoStreamDiscreteFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/H265VideoStreamFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/InputFile.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/JPEGVideoRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/JPEGVideoRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/JPEGVideoSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/Locale.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MatroskaDemuxedTrack.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MatroskaDemuxedTrack.hh
   ${${TARGET_NAME}_HOME}/liveMedia/MatroskaFile.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MatroskaFileParser.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MatroskaFileParser.hh
   ${${TARGET_NAME}_HOME}/liveMedia/MatroskaFileServerDemux.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MatroskaFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MatroskaFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/Media.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MediaSession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MediaSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MediaSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3ADU.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3ADUdescriptor.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3ADUdescriptor.hh
   ${${TARGET_NAME}_HOME}/liveMedia/MP3ADUinterleaving.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3ADURTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3ADURTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3ADUTranscoder.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3AudioFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3AudioMatroskaFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3AudioMatroskaFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/MP3FileSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3Internals.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3Internals.hh
   ${${TARGET_NAME}_HOME}/liveMedia/MP3InternalsHuffman.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3InternalsHuffman.hh
   ${${TARGET_NAME}_HOME}/liveMedia/MP3InternalsHuffmanTable.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3StreamState.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MP3StreamState.hh
   ${${TARGET_NAME}_HOME}/liveMedia/MP3Transcoder.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG1or2AudioRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG1or2AudioRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG1or2AudioStreamFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG1or2Demux.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG1or2DemuxedElementaryStream.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG1or2DemuxedServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG1or2FileServerDemux.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG1or2VideoFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG1or2VideoRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG1or2VideoRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG1or2VideoStreamDiscreteFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG1or2VideoStreamFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG2IndexFromTransportStream.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG2TransportFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG2TransportStreamFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG2TransportStreamFromESSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG2TransportStreamFromPESSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG2TransportStreamIndexFile.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG2TransportStreamMultiplexor.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG2TransportStreamTrickModeFilter.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG2TransportUDPServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG4ESVideoRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG4ESVideoRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG4GenericRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG4GenericRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG4LATMAudioRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG4LATMAudioRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG4VideoFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG4VideoStreamDiscreteFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEG4VideoStreamFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEGVideoStreamFramer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEGVideoStreamParser.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MPEGVideoStreamParser.hh
   ${${TARGET_NAME}_HOME}/liveMedia/MultiFramedRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/MultiFramedRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/OggDemuxedTrack.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/OggDemuxedTrack.hh
   ${${TARGET_NAME}_HOME}/liveMedia/OggFile.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/OggFileParser.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/OggFileParser.hh
   ${${TARGET_NAME}_HOME}/liveMedia/OggFileServerDemux.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/OggFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/OggFileServerMediaSubsession.hh
   ${${TARGET_NAME}_HOME}/liveMedia/OggFileSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/OnDemandServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/ourMD5.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/OutputFile.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/PassiveServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/ProxyServerMediaSession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/QCELPAudioRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/QuickTimeFileSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/QuickTimeGenericRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/RTCP.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/rtcp_from_spec.c
   ${${TARGET_NAME}_HOME}/liveMedia/rtcp_from_spec.h
   ${${TARGET_NAME}_HOME}/liveMedia/RTPInterface.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/RTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/RTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/RTSPClient.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/RTSPCommon.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/RTSPRegisterSender.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/RTSPServer.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/RTSPServerSupportingHTTPStreaming.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/ServerMediaSession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/SimpleRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/SimpleRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/SIPClient.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/StreamParser.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/StreamParser.hh
   ${${TARGET_NAME}_HOME}/liveMedia/StreamReplicator.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/T140TextRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/TCPStreamSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/TextRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/TheoraVideoRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/TheoraVideoRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/uLawAudioFilter.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/VideoRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/VorbisAudioRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/VorbisAudioRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/VP8VideoRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/VP8VideoRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/VP9VideoRTPSink.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/VP9VideoRTPSource.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/WAVAudioFileServerMediaSubsession.cpp
   ${${TARGET_NAME}_HOME}/liveMedia/WAVAudioFileSource.cpp
)
# Group (Filter) source files
source_group ( "Source Files\\liveMedia" FILES ${${TARGET_NAME}_SOURCES_LIVEMEDIA} )

list ( APPEND ${TARGET_NAME}_SOURCES
   ${${TARGET_NAME}_SOURCES_USAGEENVIRONMENT}
   ${${TARGET_NAME}_SOURCES_BASICUSAGEENVIRONMENT}
   ${${TARGET_NAME}_SOURCES_GROUPSOCK}
   ${${TARGET_NAME}_SOURCES_LIVEMEDIA}
)

add_library ( ${TARGET_NAME} ${${TARGET_NAME}_SOURCES} ${${TARGET_NAME}_HEADERS} )

set ( ${TARGET_NAME}_LINK_LIBRARIES "" )
if ( WIN32 )
	list ( APPEND ${TARGET_NAME}_LINK_LIBRARIES
	   ws2_32
   )
endif ()
target_link_libraries ( ${TARGET_NAME} PRIVATE ${${TARGET_NAME}_LINK_LIBRARIES} )

if ( WIN32 )
   set_target_properties ( ${TARGET_NAME} PROPERTIES DEBUG_POSTFIX "d" )
else ()
   set_target_properties ( ${TARGET_NAME} PROPERTIES DEBUG_POSTFIX "-debug" )
endif ()

install ( FILES
	${${TARGET_NAME}_HEADERS_USAGEENVIRONMENT}
	DESTINATION
	"${CMAKE_INSTALL_PREFIX}/include/UsageEnvironment"
)

install ( FILES
	${${TARGET_NAME}_HEADERS_BASICUSAGEENVIRONMENT}
	DESTINATION
	"${CMAKE_INSTALL_PREFIX}/include/BasicUsageEnvironment"
)

install ( FILES
	${${TARGET_NAME}_HEADERS_GROUPSOCK}
	DESTINATION
	"${CMAKE_INSTALL_PREFIX}/include/groupsock"
)

install ( FILES
	${${TARGET_NAME}_HEADERS_LIVEMEDIA}
	DESTINATION
	"${CMAKE_INSTALL_PREFIX}/include/liveMedia"
)

install ( TARGETS
	${TARGET_NAME}
	RUNTIME DESTINATION bin
	LIBRARY DESTINATION lib
	ARCHIVE DESTINATION lib
)
