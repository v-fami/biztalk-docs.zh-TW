---
title: AS2 事件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9de140d-8961-4c19-a2e5-14631016541f
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 824fda0d49ddfd9c5d6f6c12a379568775b8d160
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233590"
---
# <a name="as2-events"></a>AS2 事件
下表列出在 AS2 處理期間可能會在事件記錄檔中寫入的事件訊息。  
  
> [!NOTE]
>  如需下表所列的 AS2 錯誤的詳細資訊，請參閱[EDI 和 AS2 事件](../core/edi-and-as2-events.md)。  
  
|錯誤碼|條件|  
|----------------|---------------|  
|AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError|AS2 解碼器找不到產生 MDN 所需的 Disposition-Notification-Options HTTP 標頭。|  
|SynchronousMdnRequestedOnOneWayReceivePortError|組態錯誤。  對單向 HTTP 接收埠要求同步 MDN。|  
|SynchronousMdnRequestedOnOneWaySendPortError|組態錯誤。  對單向 HTTP 傳送埠要求同步 MDN。|  
|EncryptionCertNotConfiguredError|尚未針對 AS2 合作對象設定加密憑證。  AS2-從： {0} AS2-以： {1}|  
|AS2DecoderPartySigningConfigurationError|組態錯誤。  訊息簽章不符合預期值。  請連絡傳送方夥伴，並確認簽章用法。  AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"|  
|AS2DecoderExceptionEncounteredDuringProcessing|AS2 解碼器在處理過程中發生例外狀況。  訊息和例外狀況的詳細資料如下： AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"MessageType:"{3} 」 例外狀況:"\ {4\}"|  
|AS2DecoderMdnMicFailureDuringProcessing|驗證 MDN 中傳回的 MIC 值時，AS2 解碼器處理失敗。  MDN 訊息的詳細資料如下： AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"OriginalMessageID:"\ {3\}"|  
|AS2DecoderMdnSigningMismatchFailureDuringProcessing|AS2 解碼器處理失敗，因為 MDN 簽章不符合我們的要求。  MDN 訊息的詳細資料如下： AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"OriginalMessageID:"\ {3\}"|  
|AS2DecoderMdnProcessingFailureReturned|AS2 解碼器處理失敗，因為 MDN 表示 AS2 訊息處理失敗。  MDN 訊息的詳細資料如下： AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"OriginalMessageID:"\ {3\}"|  
|AS2InvalidQuotedStringHeaderError|發現無效且具引號的 HTTP 標頭。  詳細資料如下： 標頭名稱:"{0}"標頭值:"{1}"|  
|AS2MicDataStoreDuplicateMicError|錯誤：Mic 項目已經存在。|  
|AS2StreamingNonSeekableStreamError|這是不可搜尋的資料流。|  
|AS2StreamingSetLengthError|無法設定此資料流的長度。|  
|AS2StreamingWriteToReadonlyStreamError|這是唯讀資料流。|  
|AS2StreamingMethodNotImplementedError|方法或作業尚未實作。|  
|BtsMimeExceptionEncounteredDuringMessageDecoding|嘗試將 AS2 訊息解碼時發生 BTS MIME 錯誤。  AS2-從: {0}，AS2-以： {1}，MessageId: {2}，錯誤： {3}|  
|AS2DecoderPartyEncryptionConfigurationError|組態錯誤。  訊息加密不符合預期值。  請連絡傳送方夥伴，並確認加密用法。  AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"|  
|AS2DecoderPartySignatureError|組態錯誤。  訊息簽章不符合此合作對象的設定簽章。  請連絡傳送方夥伴，並確認所用的憑證。  AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"|  
|InvalidAgreementAS2FromName|此 AS2 交換的合作對象必須包含 AS2-From 的值。|  
|InvalidAgreementAS2ToName|此 AS2 交換的合作對象必須包含 AS2-To 的值。|  
|UnsupportedAS2HashAlgorithmError|不支援 AS2 訊息中指定的雜湊演算法。|  
|UnableToLocateAS2PartyError|無法存取使用限定詞的合作對象： {0} 合作對象： {1}。  錯誤： {2}|  
|UnableToLocateAS2PartyByPartyNameError|無法使用合作對象: {0} 存取合作對象。|  
|UnableToLocateAS2PartyBySendPortNameError|無法存取合作對象使用傳送埠： {0} 錯誤： {1}。|  
|InvalidAS2FromNameConfiguredError|無效的 AS2-從合作對象設定名稱： {0} 值： {1}|  
|InvalidAS2ToNameConfiguredError|無效的 AS2-若要設定合作對象名稱： {0} 值： {1}|  
|InvalidAS2FromNameHeaderReceivedError|收到無效的 AS2-From 標頭。  值： {0}|  
|InvalidAS2ToNameHeaderReceivedError|收到無效的 AS2-To 標頭。  值： {0}|  
|MissingAS2FromHeaderError|收到的 AS2 訊息不包含 AS2-From 標頭。|  
|MissingAS2ToHeaderError|收到的 AS2 訊息不包含 AS2-To 標頭。|  
|InvalidDispositionNotificationOptionToError|配置通知選項的值:"{0}"無效。  {1}|  
|InvalidReceiptDeliveryOptionError|回條傳遞選項的值:"{0}"無效。  {1}|  
|InvalidOrMissingASN1DataLengthHeader|解壓縮處理過程中發現無效或遺失的 ASN.1 資料長度欄位。|  
|InvalidOrMissingASN1TrailingBytes|解壓縮處理過程中發現無效或遺失的尾端 ASN.1 CMS 壓縮結構。|  
|InvalidASN1CompressedStructureEncountered|解壓縮處理過程中發現無效的 ASN.1 壓縮結構。|  
|InvalidOrMissingDataHeaderEncountered|解壓縮處理過程中發現無效或遺失的 ASN.1 壓縮標頭。|  
|InvalidOptionalZLibFieldEncountered|解壓縮處理過程中發現無效的 ASN.1 ZLib 壓縮欄位。|  
|InvalidOrMissingDataOIDEncountered|解壓縮處理過程中發現無效或遺失的 ASN.1 資料 OID。|  
|InvalidOrMissingZLibOIDEncountered|解壓縮處理過程中發現無效或遺失的 ASN.1 ZLib OID。|  
|InvalidOrMissingCompressedDataOIDEncountered|解壓縮處理過程中發現無效或遺失的 ASN.1 壓縮資料 OID。|  
|InvalidAdler32ChecksumInCompressedMessageError|發現無效的 Adler32 總和檢查碼。|  
|UnsupportedOctetStringLengthEncountered|發現不支援的八位元資料組字串長度。  支援的最大八位元資料組長度為 4。|  
|DecompressionFailedError|處理壓縮的 AS2 訊息時，解壓縮失敗。  錯誤： {0}|  
|DecryptionFailedError|解密 AS2 訊息時發生錯誤。|  
|IntegrityCheckFailedError|驗證 AS2 訊息時發生錯誤。  請確定所用的憑證尚未逾時或遭到撤銷。|  
|EncryptionCertificateHasBeenRevokedError|用於加密訊息的憑證已遭到撤銷。 憑證指紋: {0}|  
|DecryptionCertificateHasBeenRevokedError|用於解密訊息的憑證已遭到撤銷。 憑證指紋: {0}|  
|SigningCertificateHasBeenRevokedError|用於簽章訊息的憑證已遭到撤銷。 憑證指紋: {0}|  
|SignatureCertificateHasBeenRevokedError|用於簽章訊息的憑證已遭到撤銷。 憑證指紋: {0}|  
|CertificateMissingError|在本機憑證存放區中找不到訊息中簽章所用的憑證。 憑證指紋: {0}|  
|EmptyContentOnAS2MessageEncountered|收到空白的 AS2 訊息。  將擱置此訊息。|  
|AS2FromMatchesAS2ToError|AS2-From 值符合 AS2-To 值。|  
|GenericEdiIntException|發生 EdiInt 例外狀況。|  
|BtsMimeExceptionEncounteredDuringMessageEncoding|嘗試將訊息編碼時發生 BTS MIME 錯誤。  錯誤: {0}，HResult: \ {1 \}|  
|BtsMimeGeneralExceptionEncounteredDuringMessageEncoding|嘗試將訊息編碼時發生 BTS MIME 錯誤。  錯誤： {0}|  
|AS2StatusReportingExceptionEncountered|嘗試產生 AS2 狀態報告時發生錯誤。  錯誤： {0}|