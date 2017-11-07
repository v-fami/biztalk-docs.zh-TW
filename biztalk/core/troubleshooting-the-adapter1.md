---
title: "JD Edwards EnterpriseOne 配接器進行疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5a55e52-039a-4aea-8251-b697fd061ddc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eac716a7567930509ebfd310cdaf9874286b349c
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="troubleshooting-the-adapter"></a>配接器疑難排解
本主題所含的資訊，可協助您辨識和解決在使用 Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 時可能會遇到的問題。  
  
## <a name="cannot-use-wildcards-in-send-port-properties"></a>無法在傳送埠屬性中使用萬用字元  
 Adapter for JD Edwards Enterprise One 不支援在下列傳送埠屬性欄位中使用萬用字元：  
  
-   使用者名稱  
  
-   JDE 環境  
  
-   Host  
  
-   通訊埠  
  
-   Java_Home  
  
-   JDE JAR 檔案  
  
-   安全性伺服器名稱  
  
-   服務名稱連接  
  
-   資料來源名稱  
  
-   資料庫擁有者  
  
-   資料庫伺服器名稱  
  
-   資料庫類型  
  
-   實體資料庫名稱  
  
## <a name="connecting-to-oracle-database"></a>連線到 Oracle 資料庫  
 搭配 JD Edwards 使用 Oracle 資料庫時，您必須修改 jdeinterop.ini 檔案。 使用單一登入，[JDBj-ORACLE] 區段會定義 Oracle tnsnames 位置；必須使用資料庫參數；且 SQLNET.ORA 檔案必須存在 BizTalk Server 電腦上 (這應該會隨附在 Oracle Client 中)。  
  
 將下列項目加入至 jdeinterop.ini 檔案：  
  
1.  在 [JDBj-ORACLE] 下：  
  
    ```  
    tns=c:\Oracle\ora92\network\Admin\tnsnames.ora  
    ```  
  
2.  在 [JDBj-BOOTSTRAP DATA SOURCE] 下：  
  
    ```  
    database=sys810 [hardcode the database name. This information is available in the JDE.ini file on the JD Edwards computer.]  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [新增配接器，並建立成品](../core/adding-biztalk-adapter-for-jd-edwards-enterpriseone.md)   
 [疑難排解 JD Edwards EnterpriseOne](../core/troubleshooting-jd-edwards-enterpriseone.md)