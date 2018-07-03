---
title: 針對適用於 SAP 的資料提供者的問題進行疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, troubleshooting
- troubleshooting, Data Provider for SAP
ms.assetid: 6fe9baed-0404-4f15-b76e-88cc11c5ff46
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f481a5f71ea5677165390177eb809239961eb9e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018433"
---
# <a name="troubleshoot-issues-with-the-data-provider-for-sap"></a>針對適用於 SAP 的資料提供者的問題進行疑難排解
本節討論如何使用以解決使用時可能遭遇的操作錯誤的疑難排解技巧[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。  
  
##  <a name="BKMK_SAPUnknownParam"></a> 使用適用於 SAP 的資料提供者的未知的參數時發生錯誤  
 **問題**  
  
 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]會產生下列錯誤：  
  
```  
Microsoft.Data.SAPClient.SAPException: Failed to retrieve data from SAP server --- > Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Unknown Parameter OUT_ZDATATABLE.  
```  
  
 **原因**  
  
 不是最新的自訂 RFC、 Z_EXTRACT_DATA_OO，安裝在您的 SAP 系統。 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]使用的自訂 RFC Z_EXTRACT_DATA_OO，執行 SAP 資料表上的 SELECT 作業。  
  
 **解決方式**  
  
 您必須更新自訂 RFC 為最新可用版本。 這個 RFC、 Z_EXTRACT_DATA_OO，適用於 adapterpacknoversion。 如需如何安裝和解除安裝自訂 RFC 的詳細資訊，請參閱[安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。
  
##  <a name="BKMK_SAPOOM"></a> 記憶體不足例外狀況從 SAP 資料表選取資料時  
 **問題**  
  
 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] SAP 系統從選取的資料時，會擲回記憶體不足例外狀況。  
  
 **原因**  
  
 根據預設，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]擷取 10,000 個資料列一次。 此外，每個 SAP 系統從擷取的資料列的批次會儲存在記憶體中。 因此，  
  
- 如果從中擷取資料的資料表包含大量資料列，或  
  
- 如果資料表包含會耗用大量記憶體的資料類型的資料行  
  
  記憶體耗用量[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]大幅增加，可能會導致記憶體不足例外狀況。  
  
  **解決方式**  
  
  您可以變更 SAP 系統從擷取的資料列數目上限。 您可以藉由指定 SELECT 陳述式的 'batchsize' 選項來這麼做。 例如：  
  
```  
SELECT * FROM <tablename> OPTION 'batchsize 1000'  
```  
  
 [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]現在會只 1000 個資料列擷取一次，因此不會耗用大量的記憶體。  
  
##  <a name="BKMK_SAPQueryExcep"></a> 執行查詢： 接受具有日期值的參數時發生例外狀況  
 **問題**  
  
 當您執行查詢，使用 EXECQUERY 命令可接受的日期值的參數時，您會取得下列例外狀況：  
  
```  
ErrorCode=RFC_SYS_EXCEPTION. ErrorGroup=RFC_ERROR_SYSTEM_FAILURE.   
SapErrorMessage=Enter date in the format __.__.____.  
```  
  
 **原因**  
  
 執行時使用 EXECQUERY 命令的查詢，您一律必須以 YYYYMMDD 格式來指定日期值。  
  
 **解決方式**  
  
 請確定您指定日期值格式為 YYYYMMDD。 例如：  
  
```  
EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1='20080606'  
```  
  
##  <a name="BKMK_SAPNOVARIANT"></a> 執行查詢使用 EXECQUERY 命令 NO_VARIANT 例外狀況  
 **問題**  
  
 當您執行查詢，使用 EXECQUERY 命令時，您就會收到下列例外狀況：  
  
```  
Exception: Details: ErrorCode=RFC_EXCEPTION. ErrorGroup=RFC_ERROR_APPLICATION_EXCEPTION. SapErrorMessage=NO_VARIANT.  
AdapterErrorMessage=Error returned by RfcCallReceiveEx while calling RFC: <RFC name>  
```  
  
 **原因**  
  
 可以有兩個可能的原因，這個例外狀況：  
  
1. 您嘗試執行的查詢的 SAP 系統中定義的變數。 變化是指一組儲存執行 SAP 查詢時，您可以指定的選取準則。 比方說，您可以使用變數來指定查詢的預設值。  
  
2. 您嘗試執行未查詢的變數定義也預期要傳遞的參數值。  
  
   **解決方式**  
  
3. 基於為 1 時，請確定您指定與查詢相關聯之變數的名稱。 例如：  
  
   ```  
   EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @variant =  ‘variant1’  
   ```  
  
4. 基於為 2 時，請確定您指定查詢命令時提供空的參數名稱和值。 例如，"myquery 」 查詢不需要任何參數來執行，如果 EXECQUERY 命令必須指定為：  
  
   ```  
   EXECQUERY myquery @usergroup='mygroup',@P1 = 'dummy_value'  
   ```  
  
## <a name="see-also"></a>另請參閱  
[SAP 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)