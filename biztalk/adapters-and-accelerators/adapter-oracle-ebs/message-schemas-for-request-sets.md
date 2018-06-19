---
title: 要求的訊息結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bba9677d-ee94-4da5-8611-b1e47f2f3798
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fd81ee75088b41a182c5a2aa675266420f8f32f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217094"
---
# <a name="message-schemas-for-request-sets"></a>要求的訊息結構描述
Oracle E-business Suite 中的 Oracle 應用程式中設定每個要求會呈現為中的作業[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。  
  
## <a name="message-structure-of-request-set-operation"></a>要求的訊息結構，設定作業  
 要求設定中顯示的作業會遵循要求-回應訊息交換模式。 下表顯示這些要求和回應訊息的結構。  
  
> [!NOTE]
>  在資料表之後，請參閱實體描述。  
  
|作業|XML 訊息|Description|  
|---------------|-----------------|-----------------|  
|[Request_Set_Name]要求|`<?xml version="1.0" encoding="utf-8" ?> <[Request_Set_Name] xmlns="[VERSION]/RequestSets/[APP_SHORT_NAME]/">   <SetRelClassOptions>     <Application>[value]</Application>     <ClassName>[value]</ClassName>     <CancelOrHold>[value]</CancelOrHold>     <StaleDate>[value]</StaleDate>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRelClassOptions>   <SetPrintOptions>     <Printer>[value]</Printer>     <Style>[value]</Style>     <Copies>[value]</Copies>     <SaveOutput>[value]</SaveOutput>     <PrintTogether>[value]</PrintTogether>     <ContinueOnFail>[value]</ContinueOnFail>   </SetPrintOptions>   <SetRepeatOptions>     <RepeatTime>[value]</RepeatTime>     <RepeatInterval>[value]</RepeatInterval>     <RepeatUnit>[value]</RepeatUnit>     <RepeatType>[value]</RepeatType>     <RepeatEndTime>[value]</RepeatEndTime>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRepeatOptions>   <SetNlsOptions>     <Language>[value]</Language>     <Territory>[value]</Territory>     <ContinueOnFail>[value]</ContinueOnFail>   </SetNlsOptions>   <StartTime><[value]</StartTime>   <[CONCURRENT_PROGRAM_NAME1]>[value]</[CONCURRENT_PROGRAM_NAME1]>   <[CONCURRENT_PROGRAM_NAME2]>[value]</[CONCURRENT_PROGRAM_NAME2]>   … </[Request_Set_Name]>`|-[Request_Set_Name] 作業會採用標準的五個參數： `SetRelClassOptions`， `SetPrintOptions`， `SetRepeatOptions`， `SetNlsOptions`，和`StartTime`。<br /><br /> -`ContinueOnFail`參數會指出是否要求組提交事件應該繼續還是擲回例外狀況案例中的父參數 (`SetRelClassOptions`， `SetPrintOptions`，`SetRepeatOptions`或`SetNlsOptions`) 失敗。 您可以指定**True** （繼續） 或**False** （擲回例外狀況）。<br /><br /> -若為每個參數的詳細資訊，請參閱[作業要求集](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md)。|  
|[Request_Set_Name]回應|`<?xml version="1.0" encoding="utf-8" ?> <[Request_Set_Name]Response xmlns="[VERSION]/RequestSets/[APP_SHORT_NAME]">   <[Request_Set_Name]Result>[value]</[Request_Set_Name]Result> </[Request_Set_Name]Response>`|Oracle E-business Suite 的回應包含並行要求識別碼。|  
  
 實體描述：  
  
 [版本] = http://schemas.microsoft.com/OracleEBS/2008/05  
  
 執行個體時提供 SQL Server 登入。  
  
 [CONCURRENT_PROGRAM_NAME] = 並行要求集中包含的程式。  
  
## <a name="message-actions-for-request-sets"></a>要求的訊息動作  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]要求組會使用下列的訊息動作。  
  
> [!NOTE]
>  在資料表之後，請參閱實體描述。  
  
|訊息|動作|範例|  
|-------------|------------|-------------|  
|要求設定要求|RequestSets / [APP_SHORT_NAME] / [REQUESTSET_SHORT_NAME]|RequestSets/SQLGL/FNDRSSUB965|  
|要求設定回應|RequestSets / [APP_SHORT_NAME] / [REQUESTSET_SHORT_NAME]] / 回應|RequestSets/SQLGL/FNDRSSUB965/回應|  
  
 實體描述：  
  
 [APP_SHORT_NAME] = 應用程式簡短名稱。  
  
 [REQUESTSET_SHORT_NAME] = 要求設定的簡短名稱。  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)