---
title: BAM 活動建立追蹤 EDI AS2 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a10ab846-0fbb-46f5-920e-cb2b5be75814
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7da7ac08a8f26e21b2c648670730db136392471
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008895"
---
# <a name="bam-activities-created-to-track-edi-as2-messages"></a>建立追蹤 EDI AS2 訊息的 BAM 活動
BizTalk Server 包含的 BAM 活動所建立的 EDI 和 AS2 狀態報告。 這些活動會決定狀態報告中顯示的資料。 本主題會描述 BAM 活動及其中所定義的欄位，並描述針對 BAM 活動內之特定欄位所定義的列舉值。  
  
 建立自訂 BAM 活動即可建立自訂狀態報告。 自訂活動可根據其中一個標準活動。 也可以藉由查詢 BizTalkDTADb 資料庫中的 EdiMessageContent 資料表，從自訂狀態報告顯示訊息的內容。 如需詳細資訊，請參閱以下的「查詢 EdiMessageContent 資料表」一節。  
  
> [!CAUTION]
>  修改 BAM 活動可能會影響 BizTalk EDI 和 AS2 執行階段的處理 (視活動而定)。  
  
## <a name="bam-activities-used-in-status-reporting"></a>用於狀態報告中的 BAM 活動  
 為了追蹤 EDI/AS2 訊息而建立的 BAM 活動，會包含於 BAMPrimaryImport 資料庫內做為檢視。 下列資料表列出 BAM 活動及其中的資料行：  
  
|BAM 活動|欄位|  
|------------------|------------|  
|AS2InterchangeActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> 方向<br /><br /> MessageID<br /><br /> AS2From<br /><br /> AS2To<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> LastModified|  
|AS2MdnActivity|RecordID<br /><br /> ActivityID<br /><br /> AS2PartyRole<br /><br /> AS2From<br /><br /> AS2To<br /><br /> MessageID<br /><br /> MdnDateTime<br /><br /> MdnDispositionType<br /><br /> DispositionModifierExtType<br /><br /> DispositionModifierExtDescription<br /><br /> MdnEncryptionType<br /><br /> MdnSignatureType<br /><br /> MdnPayloadContentKey<br /><br /> MdnWireContentKey<br /><br /> MdnMicValue<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> LastModified|  
|AS2MessageActivity|RecordID<br /><br /> ActivityID<br /><br /> ReceiverPartyName<br /><br /> SenderPartyName<br /><br /> AS2PartyRole<br /><br /> AS2From<br /><br /> AS2To<br /><br /> MessageID<br /><br /> MessageDateTime<br /><br /> BTSInterchangeID<br /><br /> BTSMessageID<br /><br /> MdnProcessingStatus<br /><br /> MessageEncryptionType<br /><br /> IsMdnExpected<br /><br /> MicAlgorithmType<br /><br /> MessageSignatureType<br /><br /> MessagePayloadContentKey<br /><br /> MessageWireContentKey<br /><br /> MessageMicValue<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> IsAS2MessageDuplicate<br /><br /> DaysToCheckDuplicate<br /><br /> FileName<br /><br /> TrackingActivityID<br /><br /> LastModified|  
|BatchingActivity|RecordID<br /><br /> ActivityID<br /><br /> BatchStatus<br /><br /> DestinationPartyID<br /><br /> DestinationPartyName<br /><br /> ActivationTime<br /><br /> BatchOccurrenceCount<br /><br /> EdiEncodingType<br /><br /> BatchType<br /><br /> TargetedBatchCount<br /><br /> ScheduledReleaseTime<br /><br /> BatchElementCount<br /><br /> RejectedBatchElementCount<br /><br /> BatchSize<br /><br /> LastBatchAction<br /><br /> CreationTime<br /><br /> ReleaseTime<br /><br /> BatchReleaseType<br /><br /> BatchServiceID<br /><br /> ActivationMessageID<br /><br /> ReleaseMessageID<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> BatchCorrelationID<br /><br /> BatchName<br /><br /> BatchID<br /><br /> LastModified|  
|BatchInterchangeActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverPartyName<br /><br /> SenderPartyName<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> 方向<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> BatchCorrelationID<br /><br /> LastModified|  
|BusinessMessageJournal|RecordID<br /><br /> ActivityID<br /><br /> MessageTrackingID<br /><br /> ActionType<br /><br /> ContainerActivityID<br /><br /> ContainerType<br /><br /> BTSInterchangeID<br /><br /> BTSMessageId<br /><br /> BTSServiceInstanceId<br /><br /> BTSHostName<br /><br /> RoutedToPartyName<br /><br /> LinkedMessageTrackingID<br /><br /> TimeCreated<br /><br /> LastModified|  
|FunctionalAckActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeActivityID<br /><br /> GroupControlNo<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> 方向<br /><br /> AckProcessingStatus<br /><br /> AckStatusCode<br /><br /> DeliveredTSCount<br /><br /> AcceptedTSCount<br /><br /> AckIcn<br /><br /> AckIcnDate<br /><br /> AckIcnTime<br /><br /> ErrorCode1<br /><br /> ErrorCode2<br /><br /> ErrorCode3<br /><br /> ErrorCode4<br /><br /> ErrorCode5<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> LastModified|  
|FunctionalGroupInfo|RecordID<br /><br /> ActivityID<br /><br /> InterchangeActivityID<br /><br /> GroupControlNo<br /><br /> FunctionalIDCode<br /><br /> TSCount<br /><br /> LastModified|  
|InterchangeAckActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> 方向<br /><br /> AckProcessingStatus<br /><br /> AckStatusCode<br /><br /> AckIcn<br /><br /> AckIcnDate<br /><br /> AckIcnTime<br /><br /> AckNoteCode1<br /><br /> AckNoteCode2<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> AckCorrelationId<br /><br /> LastModified|  
|InterchangeStatusActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> ReceiverPartyName<br /><br /> SenderPartyName<br /><br /> InterchangeDateTime<br /><br /> 方向<br /><br /> AckStatusCode<br /><br /> GroupCount<br /><br /> EdiMessageType<br /><br /> PortID<br /><br /> IsInterchangeAckExpected<br /><br /> IsFunctionalAckExpected<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> AckCorrelationId<br /><br /> TsCorrelationId<br /><br /> LastModified|  
|ResendJournalActivity|RecordID<br /><br /> ActivityID<br /><br /> TrackingActivityId<br /><br /> ResendIndex<br /><br /> ResendStatus<br /><br /> BTSInterchangeID<br /><br /> LastModified|  
|ResendTrackingActivity|RecordID<br /><br /> ActivityID<br /><br /> CorrelationId<br /><br /> AdapterPrefix<br /><br /> ResendCount<br /><br /> MaxResendCount<br /><br /> ResendInterval<br /><br /> MaxRetryCount<br /><br /> RetryInterval<br /><br /> MessageContentID<br /><br /> ResendTimeout<br /><br /> RetryTimeout<br /><br /> BTSInterchangeID<br /><br /> LastModified|  
|TransactionSetActivity|RecordID<br /><br /> ActivityID<br /><br /> InterchangeControlNo<br /><br /> ReceiverID<br /><br /> SenderID<br /><br /> ReceiverQ<br /><br /> SenderQ<br /><br /> InterchangeDateTime<br /><br /> 方向<br /><br /> ReceiverPartyName<br /><br /> SenderPartyName<br /><br /> ApplicationSender<br /><br /> ApplicationReceiver<br /><br /> GroupDateTime<br /><br /> GroupControlNo<br /><br /> TransactionSetId<br /><br /> DocType<br /><br /> TransactionSetControlNo<br /><br /> AckStatusCode<br /><br /> BatchProcessing<br /><br /> ProcessingDateTime<br /><br /> GroupOrdinal<br /><br /> TransactionSetOrdinal<br /><br /> MessageContentKey<br /><br /> TimeCreated<br /><br /> RowFlags<br /><br /> TsCorrelationId<br /><br /> LastModified|  
  
## <a name="data-enumerations-in-the-bamprimaryimport-database"></a>BAMPrimaryImport 資料庫中的資料列舉  
 有些 EDI 和 AS2 資料會以列舉的方式儲存於 BAMPrimaryImport 資料庫的資料表內。 資料會以文字的方式顯示於狀態報告。 這些值如下所述：  
  
|欄位|列舉值|  
|-----------|-----------------|  
|AckProcessingStatus|NotExpected = -1<br /><br /> 預期 = 0<br /><br /> Received = 1<br /><br /> Sent = 2<br /><br /> Generated = 3|  
|AS2PartyRole|All = 0<br /><br /> Receiver = 1<br /><br /> Sender = 2|  
|BatchAction|Creation = 0<br /><br /> Activation = 1<br /><br /> ElementReference = 2<br /><br /> Release = 3<br /><br /> Override = 4<br /><br /> Termination = 5<br /><br /> 傳送 = 6<br /><br /> ToBeReleased = 7|  
|BatchStatus|所有 =-1<br /><br /> Defined = 0<br /><br /> 作用中<br /><br /> Released<br /><br /> 已完成|  
|BatchType|ScheduleBased = 0<br /><br /> MessagesCountInGroup = 1<br /><br /> MessagesCountIn<br />交換 = 2<br /><br /> CharacterCount = 3<br /><br /> ExternalTrigger = 4|  
|方向|All = 0<br /><br /> Receive = 1<br /><br /> Send = 2|  
|DisplayAckStatusCode|所有 = 100<br /><br /> Accepted = 0<br /><br /> PartiallyAccepted = 1<br /><br /> Rejected = -1<br /><br /> AckExpected = 500<br /><br /> AckNotExpected = 600|  
|DispositionModifierExt<br />Description|Not Valued = 1<br /><br /> Authentication Failed = 2<br /><br /> Decryption Failed = 3<br /><br /> 不足的訊息<br />安全性 = 4<br /><br /> Integrity Check Failed = 5<br /><br /> 未預期的處理 <br />錯誤 = 6|  
|DispositionModifierExt<br />類型|Not Valued = 1<br /><br /> Error = 2<br /><br /> Warning = 3|  
|EdiMessageType|X12,<br /><br /> Edifact,<br /><br /> Unknown|  
|IsMdnExpected|MDN is not expected = 0<br /><br /> MDN is expected = 1|  
|MdnDispositionType|Processed = 1<br /><br /> Failed = 2|  
|MdnProcessingStatus|All = 0<br /><br /> Processed = 1<br /><br /> Failed = 2<br /><br /> Expected = 3<br /><br /> Not Expected = 4|  
|MessageEncryptionType|Message is not encrypted = 0<br /><br /> Message is encrypted = 1|  
|MessageSignatureType|Message is not signed = 0<br /><br /> Message is signed = 1|  
|MicAlgorithmType|Unknown type = -1<br /><br /> SHA1 = 1<br /><br /> MD5 = 2|  
  
## <a name="businessmessagejournal-bam-activity"></a>BusinessMessageJournal BAM 活動  
 BusinessMessageJournal BAM 活動可讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將包含交易集的已接收 EDI 交換，與包含同一個交易集的外寄批次交換產生相互關聯。 如需詳細資訊，請參閱[相互關聯的內送交易集與外寄批次](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md)。  
  
##  <a name="BKMK_Query"></a>查詢 EdiMessageContent 資料表  
 BizTalkDTADb 資料庫中的 EdiMessageContent 資料表，儲存了訊息內容以及訊息中繼資料。 您也可以從自訂狀態報告，查詢 EdiMessageContent 資料表以顯示訊息的內容。 這和產品中部分狀態報告讓您顯示訊息內容的方式類似，例如，AS2 訊息和相互關聯的 MDN 狀態報告可讓您顯示訊息電傳格式。  
  
 您使用對應至 EdiMessageContent 資料表中 ContentKey 資料行之 BAM 活動的索引鍵資料行，便可以從自訂 BAM 活動連結至 EdiMessageContent 資料表。 例如，若要從 AS2MessageActivity BAM 活動連結至 EdiMessageContent 資料表，必須使用 MessagePayloadContentKey 資料行或 MessageWireContentKey 資料行連結至 ContentKey 資料行。  
  
|Table|資料行|  
|-----------|-------------|  
|EdiMessageContent<br /><br /> (在 BizTalkDTADb 資料庫中)|ContentKey<br /><br /> MessageFormat<br /><br /> ContentType<br /><br /> Charset<br /><br /> TimeCreated<br /><br /> TimeInserted<br /><br /> IsOrphaned<br /><br /> ContentBinary|  
  
## <a name="see-also"></a>請參閱  
 [資料如何儲存 EDI 和 AS2 狀態報告](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)   
 [使內送交易集與外寄批次相互關聯](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md)