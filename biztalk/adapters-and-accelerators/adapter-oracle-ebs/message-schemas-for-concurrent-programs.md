---
title: 並行程式的訊息結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3c5709d5-e2b3-485b-9cdd-004985972ba1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f475fce04e796e633359c846c339f521b6f74a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217230"
---
# <a name="message-schemas-for-concurrent-programs"></a>並行程式的訊息結構描述
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]呈現同時做為作業執行的程式。 並行程式公開為作業，以及[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]也會提供諸如下列三種的標準作業： Get_Status、 Wait_For_Request 和 Submit_Request。 如需這些作業，同時執行之程式的相關資訊，請參閱[上同時執行之程式的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)。  
  
## <a name="message-structure-of-concurrent-program-operations"></a>並行程式作業的訊息結構  
 並行程式中顯示的作業會遵循要求-回應訊息交換模式。 下表顯示這些要求和回應訊息的結構。  
  
> [!NOTE]
>  在資料表之後，請參閱實體描述。  
  
|作業|XML 訊息|Description|  
|---------------|-----------------|-----------------|  
|[Concurrent_Program_Name]要求|`<?xml version="1.0" encoding="utf-8" ?> <[Concurrent_Program_Name] xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]/">   <SetOptions>     <Implicit>[value]</Implicit>     <Protected>[value]</Protected>     <Language>[value]</Language>     <Territory>[value]</Territory>     <ContinueOnFail>[value]</ContinueOnFail>   </SetOptions>   <SetPrintOptions>     <Printer>[value]</Printer>     <Style>[value]</Style>     <Copies>[value]</Copies>     <SaveOutput>[value]</SaveOutput>     <PrintTogether>[value]</PrintTogether>     <ContinueOnFail>[value]</ContinueOnFail>   </SetPrintOptions>   <SetRepeatOptions>     <RepeatTime>[value]</RepeatTime>     <RepeatInterval>[value]</RepeatInterval>     <RepeatUnit>[value]</RepeatUnit>     <RepeatType>[value]</RepeatType>     <RepeatEndTime>[value]</RepeatEndTime>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRepeatOptions>   <Description>[value]</Description>   <StartTime><[value]</StartTime>   <[CONCURRENT_PROGRAM_ARGUMENT1]>[value]</[CONCURRENT_PROGRAM_ARGUMENT1]>   <[CONCURRENT_PROGRAM_ARGUMENT2]>[value]</[CONCURRENT_PROGRAM_ARGUMENT2]>   … </[Concurrent_Program_Name]>`|-[Concurrent_Program_Name] 作業會採用標準的五個參數： *SetOptions*， *SetPrintOptions*， *SetRepeatOptions*，*描述*，和*StartTime*。<br /><br /> - *ContinueOnFail*參數指出是否同時並存要求送出應該繼續案例中的父參數 (*SetOptions*， *SetPrintOptions*或*SetRepeatOptions*) 失敗，或是否應該擲回例外狀況。 您可以指定**True** （繼續） 或**False** （擲回例外狀況）。<br /><br /> -若為每個參數的詳細資訊，請參閱[上同時執行之程式的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)。|  
|[Concurrent_Program_Name]回應|`<?xml version="1.0" encoding="utf-8" ?> <[Concurrent_Program_Name]Response xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <[Concurrent_Program_Name]Result>[value]</[Concurrent_Program_Name]Result> </[Concurrent_Program_Name]Response>`|Oracle E-business Suite 的回應包含並行要求識別碼。|  
|Get_Status 要求|`<?xml version="1.0" encoding="utf-8" ?> <GetStatusForConcurrentProgram xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <RequestId>[value]</RequestId>  </GetStatusForConcurrentProgram>`|此 Get_Status 要求訊息會並行程式的要求識別碼做為輸入。|  
|Get_Status 回應|`<?xml version="1.0" encoding="utf-8" ?> <GetStatusForConcurrentProgramResponse xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <GetStatusForConcurrentProgramResult>[value]</GetStatusForConcurrentProgramResult>    <Phase>[value]</Phase>    <Status>[value]</Status>    <DevPhase>[value]</DevPhase>    <DevStatus>[value]</DevStatus>    <Message>[value]</Message>  </GetStatusForConcurrentProgramResponse>`|此 Get_Status 回應訊息傳回要求階段/狀態以及完成訊息的並行處理的程式。<br /><br /> 如需每個參數的詳細資訊，請參閱[上同時執行之程式的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)。|  
|Wait_For_Request 要求|`<?xml version="1.0" encoding="utf-8" ?> <WaitForRequestForConcurrentProgram xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <RequestId>[value]</RequestId>   <Interval>[value]</Interval>   <MaxWait>[value]</MaxWait>    </WaitForRequestForConcurrentProgram>`|如需每個參數的詳細資訊，請參閱[上同時執行之程式的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)。|  
|Wait_For_Request 回應|`<?xml version="1.0" encoding="utf-8" ?> <WaitForRequestForConcurrentProgramResponse xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <WaitForRequestForConcurrentProgramResult>[value]</WaitForRequestForConcurrentProgramResult>    <Phase>[value]</Phase>    <Status>[value]</Status>    <DevPhase>[value]</DevPhase>    <DevStatus>[value]</DevStatus>    <Message>[value]</Message>    </WaitForRequestForConcurrentProgramResponse>`|此 Wait_For_Request 回應訊息傳回要求階段/狀態以及完成訊息的並行處理的程式。<br /><br /> 如需每個參數的詳細資訊，請參閱[上同時執行之程式的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)。|  
|Submit_Request 要求|`<?xml version="1.0" encoding="utf-8" ?> <SubmitRequestForConcurrentProgram xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <SetOptions>     <Implicit>[value]</Implicit>     <Protected>[value]</Protected>     <Language>[value]</Language>     <Territory>[value]</Territory>     <ContinueOnFail>[value]</ContinueOnFail>   </SetOptions>   <SetPrintOptions>     <Printer>[value]</Printer>     <Style>[value]</Style>     <Copies>[value]</Copies>     <SaveOutput>[value]</SaveOutput>     <PrintTogether>[value]</PrintTogether>     <ContinueOnFail>[value]</ContinueOnFail>   </SetPrintOptions>   <SetRepeatOptions>     <RepeatTime>[value]</RepeatTime>     <RepeatInterval>[value]</RepeatInterval>     <RepeatUnit>[value]</RepeatUnit>     <RepeatType>[value]</RepeatType>     <RepeatEndTime>[value]</RepeatEndTime>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRepeatOptions>     <Program>[value]</Program>   <Description>[value]</Description>   <StartTime>[value]</StartTime>   <Arguments>[array_of_strings</Arguments>    </SubmitRequestForConcurrentProgram>`|如需每個參數的詳細資訊，請參閱[上同時執行之程式的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)。|  
|Submit_Request 回應|`<?xml version="1.0" encoding="utf-8" ?> <SubmitRequestForConcurrentProgramResponse xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <SubmitRequestForConcurrentProgramResult>[value]</SubmitRequestForConcurrentProgramResult>  </SubmitRequestForConcurrentProgramResponse>`|如果送出要求順利完成，將回應訊息傳回並行要求識別碼。 否則，它會傳回"0"。|  
  
 實體描述：  
  
 [版本] = http://schemas.microsoft.com/OracleEBS/2008/05  
  
 [APP_SHORT_NAME] = 應用程式簡短名稱  
  
 [CONCURRENT_PROGRAM_ARGUMENT] = Oracle E-business Suite 中所定義，並行程式所預期的引數  
  
## <a name="message-actions-for-concurrent-programs"></a>並行程式的訊息動作  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]並行程式會使用下列的訊息動作。  
  
> [!NOTE]
>  在資料表之後，請參閱實體描述。  
  
|訊息|動作|範例|  
|-------------|------------|-------------|  
|[Concurrent_Program_Name]要求|ConcurrentPrograms / [APP_SHORT_NAME] / [CONCURRENT_PROGRAM_SHORT_NAME]|ConcurrentPrograms/SQLGL/ADSFINS|  
|[Concurrent_Program_Name]回應|ConcurrentPrograms / [APP_SHORT_NAME] / [CONCURRENT_PROGRAM_SHORT_NAME] / 回應|ConcurrentPrograms/SQLGL/ADSFINS/回應|  
|Get_Status 要求|ConcurrentPrograms / [APP_SHORT_NAME] / GetStatusForConcurrentProgram|ConcurrentPrograms/SQLGL/GetStatusForConcurrentProgram|  
|Get_Status 回應|ConcurrentPrograms / [APP_SHORT_NAME] / GetStatusForConcurrentProgram/回應|ConcurrentPrograms/SQLGL/GetStatusForConcurrentProgram/回應|  
|Wait_For_Request 要求|ConcurrentPrograms / [APP_SHORT_NAME] / WaitForRequestForConcurrentProgram|ConcurrentPrograms/SQLGL/WaitForRequestForConcurrentProgram|  
|Wait_For_Request 回應|ConcurrentPrograms / [APP_SHORT_NAME] / WaitForRequestForConcurrentProgram/回應|ConcurrentPrograms/SQLGL/WaitForRequestForConcurrentProgram/回應|  
|Submit_Request 要求|ConcurrentPrograms / [APP_SHORT_NAME] / SubmitRequestForConcurrentProgram|ConcurrentPrograms/SQLGL/SubmitRequestForConcurrentProgram|  
|Submit_Request 回應|ConcurrentPrograms / [APP_SHORT_NAME] / SubmitRequestForConcurrentProgram/回應|ConcurrentPrograms/SQLGL/SubmitRequestForConcurrentProgram/回應|  
  
 實體描述：  
  
 [APP_SHORT_NAME] = 應用程式簡短名稱  
  
 [CONCURRENT_PROGRAM_SHORT_NAME] = 並行程式簡短名稱  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)