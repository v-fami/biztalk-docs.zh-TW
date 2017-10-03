---
title: "與繫結檔案更新現有的組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, updating
- binding files, rules
- artifacts, binding files
- binding files, unbinding
- binding files, customizing
- artifacts, updating
ms.assetid: 11580e59-7147-42d0-a976-f6b5e6933d24
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03b17ee54f053fb6a81b3855ffbcbcc1e776f513
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="updating-an-existing-configuration-with-a-binding-file"></a>使用繫結檔案更新現有的組態
繫結檔案中的資訊會取代現有的組態資訊。 如果繫結檔案中的成品名稱與現有組態中的成品名稱相符，則當您匯入繫結檔案時，繫結檔案中的成品將會更新現有組態中的成品。  
  
 以繫結檔案成品更新現有成品時，必須遵循特定規則。 本主題將討論以繫結檔案內的成品更新現有組態內的成品時，應遵循的規則。  
  
 本節假設匯入繫結檔案時，該檔案中的值都是有效的，暫不討論任何有關內含無效值之繫結檔案的實例。  
  
## <a name="rules-followed-by-biztalk-server-when-updating-a-configuration-with-a-binding-file"></a>以繫結檔案更新組態時，BizTalk Server 所遵循的規則  
 以繫結檔案中的相符成品更新現有成品時，BizTalk Server 會遵循特定規則。 一般而言，會套用下列規則：  
  
-   透過 BizTalk Server 使用者介面 (例如，[BizTalk Server 管理主控台] 或 [BizTalk 總管]) 設定成品時所公開的文字方塊和核取方塊，必須設定為特定值或者是空的。 繫結檔案中提供的成品值將會分別設定更新項目的使用者介面值。  
  
-   透過 BizTalk Server 使用者介面設定成品時所公開的下拉式清單方塊，必須設定為特定值或設定為「無」。 繫結檔案中提供的成品值將會分別設定更新項目的使用者介面值。  
  
-   透過 BizTalk Server 使用者介面設定成品時所公開的資料格檢視，將以繫結檔案中的對應項目清單來更新。 除非資料格檢視清單繫結至連接埠或接收位置，否則與資料格檢視關聯的清單一律由繫結檔案中的清單加以覆寫。 在此情況下，繫結檔案中的清單會和現有的資料格檢視清單合併。  
  
-   繫結檔案中的成品是由主索引鍵值所識別。 在使用者介面中，無法將成品主索引鍵關聯的值設定為 Null，因此必須為繫結檔案中的所有成品設定主索引鍵值。 如果繫結檔案中與成品主索引鍵關聯的值，符合現有組態中與成品主索引鍵關聯的值，則將這些成品視為相同或相符。 如果繫結檔案成品和現有成品相同，則以繫結檔案成品來更新現有成品，如下表所述。 如果繫結檔案中的成品包含唯一主索引鍵值，則匯入繫結檔案時，會在 BizTalk Server 組態中建立新成品。  
  
 如果您要透過匯入繫結檔案，以其中相符的成品來更新現有組態成品，下表描述了預期的行為，可供參考。  
  
|成品類型|屬性|指定屬性的可能相符項目|使用者介面欄位|從繫結檔案匯入相符成品的影響|  
|-------------------|--------------|------------------------------------------------|--------------------------|--------------------------------------------------------------|  
|**合作對象**|名稱|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|主要金鑰|  
||Aliases|Min Occurs: 0<br /><br /> Max Occurs: *|資料格|以繫結檔案中的別名清單來覆寫別名清單。|  
||傳送埠|Min Occurs: 0<br /><br /> Max Occurs: *|資料格|將此合作對象現有的連接埠清單，與繫結檔案中，該合作對象的連接埠清單合併。|  
||憑證一般名稱和指紋|Min Occurs: 0<br /><br /> Max Occurs: 1<br /><br /> (每個屬性)|文字方塊|以繫結檔案中指定的值來覆寫這些值。 如果繫結檔案中沒有這些值，則設定為 Null。|  
|**協調流程**|Description|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|以繫結檔案中指定的值來覆寫這個值。|  
||Host|Min Occurs: 0<br /><br /> Max Occurs: 1|下拉式清單|以繫結檔案中指定的值來覆寫這個值。 如果繫結檔案中沒有這個值，則設定為 Null。|  
||輸入連接埠和輸出連接埠|Min Occurs: 0<br /><br /> Max Occurs: *|下拉式清單|將邏輯連接埠繫結至現有的實體連接埠。 實體連接埠可以存在於下列位置：<br /><br /> -在群組中。<br />-在應用程式。<br />-繫結檔案中。<br /><br /> （選擇性） 若要設定連接埠**無**。 如果設定為**無**然後邏輯連接埠未繫結到任何資源。|  
||追蹤屬性核取方塊|Min Occurs: 1<br /><br /> Max Occurs: 1<br /><br /> (每個屬性)|核取方塊|以繫結檔案中指定的值來覆寫這些值。|  
|**傳送埠群組**|名稱|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|主要金鑰|  
||傳送埠|Min Occurs: 0<br /><br /> Max Occurs: *|資料格|將此傳送埠群組現有的連接埠清單，與繫結檔案中，該傳送埠群組的連接埠清單合併。|  
||篩選|Min Occurs: 0<br /><br /> Max Occurs: *|資料格|以繫結檔案中為此傳送埠群組指定的篩選條件清單，覆寫該傳送埠群組現有的篩選條件清單。|  
|**傳送埠**|名稱|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|主要金鑰|  
||傳輸 - 類型|Min Occurs: 1<br /><br /> Max Occurs: 1|下拉式清單|以繫結檔案中指定的值來覆寫這個值。|  
||傳輸 - 傳送處理常式|Min Occurs: 1<br /><br /> Max Occurs: 1|下拉式清單|以繫結檔案中指定的值來覆寫這個值。|  
||傳送管線|Min Occurs: 1<br /><br /> Max Occurs: 1|下拉式清單|以繫結檔案中指定的值來覆寫這個值。|  
||重試計數、重試間隔和優先順序|Min Occurs: 1<br /><br /> Max Occurs: 1<br /><br /> (每個屬性)|捲動方塊|以繫結檔案中指定的值來覆寫這些值。|  
||排序的傳遞|Min Occurs: 1<br /><br /> Max Occurs: 1|核取方塊|以繫結檔案中指定的值來覆寫這個值。|  
||啟用失敗訊息的路由|Min Occurs: 1<br /><br /> Max Occurs: 1|核取方塊|以繫結檔案中指定的值來覆寫這個值。|  
||啟用服務窗口|Min Occurs: 1<br /><br /> Max Occurs: 1|核取方塊|以繫結檔案中指定的值來覆寫這個值。|  
||服務窗口開始時間和服務窗口停止時間|Min Occurs: 1<br /><br /> Max Occurs: 1|捲動方塊|以繫結檔案中指定的值來覆寫這些值。|  
||地圖|Min Occurs: 0<br /><br /> Max Occurs: *|資料格|以繫結檔案中為此傳送埠指定的對應清單，覆寫該傳送埠現有的對應清單。|  
||篩選|Min Occurs: 0<br /><br /> Max Occurs: *|資料格|以繫結檔案中為此傳送埠指定的篩選條件清單，覆寫該傳送埠現有的篩選條件清單。|  
||憑證一般名稱|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|以繫結檔案中指定的值來覆寫這個值。|  
||憑證指紋|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|以繫結檔案中指定的值來覆寫這個值。|  
||追蹤|Min Occurs: 0<br /><br /> Max Occurs: 1|核取方塊|以繫結檔案中指定的值來覆寫這個值。|  
||備份傳輸類型|Min Occurs: 0<br /><br /> Max Occurs: 1|下拉式清單|以繫結檔案中指定的值來覆寫這個值。|  
||備份傳輸 URI|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|以繫結檔案中指定的值來覆寫這個值。 只有在備份傳輸的 [類型] 已設定時才有效。|  
||備份傳輸傳送處理常式|Min Occurs: 1<br /><br /> Max Occurs: 1|下拉式清單|以繫結檔案中指定的值來覆寫這個值。 只有在備份傳輸的 [類型] 已設定時才有效。|  
||備份傳輸重試計數|Min Occurs: 1<br /><br /> Max Occurs: 1|捲動方塊|以繫結檔案中指定的值來覆寫這個值。 只有在備份傳輸的 [類型] 已設定時才有效。|  
||備份傳輸重試間隔|Min Occurs: 1<br /><br /> Max Occurs: 1|捲動方塊|以繫結檔案中指定的值來覆寫這個值。 只有在備份傳輸的 [類型] 已設定時才有效。|  
||備份傳輸啟用服務窗口|Min Occurs: 1<br /><br /> Max Occurs: 1|核取方塊|以繫結檔案中指定的值來覆寫這個值。 只有在備份傳輸的 [類型] 已設定時才有效。|  
||備份傳輸服務窗口開始時間和服務窗口停止時間|Min Occurs: 1<br /><br /> Max Occurs: 1|捲動方塊|以繫結檔案中指定的值來覆寫這些值。 只有在備份傳輸的 [類型] 及 [啟用服務窗口] 值都已設定時才有效。|  
|**接收埠**|名稱|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|主要金鑰|  
||驗證設定 (選項按鈕)|Min Occurs: 1<br /><br /> Max Occurs: 1|選項按鈕|以繫結檔案中指定的值來覆寫這個值。|  
||啟用失敗訊息的路由|Min Occurs: 1<br /><br /> Max Occurs: 1|核取方塊|以繫結檔案中指定的值來覆寫這個值。|  
||Description|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|以繫結檔案中指定的值來覆寫這個值。|  
||接收位置|Min Occurs: 0<br /><br /> Max Occurs: *|資料格|以繫結檔案中為此接收埠指定的接收位置清單，覆寫該接收埠現有的接收位置清單。 如果繫結檔案中的所有接收位置都已存在於群組中，則匯入會失敗。|  
||地圖|Min Occurs: 0<br /><br /> Max Occurs: *|資料格|以繫結檔案中為此接收埠指定的對應清單，覆寫該接收埠現有的對應清單。|  
||追蹤 - 追蹤訊息內文和追蹤訊息屬性|Min Occurs: 1<br /><br /> Max Occurs: 1<br /><br /> (每個核取方塊)|核取方塊|以繫結檔案中指定的值來覆寫這些值。|  
|**接收位置**|名稱|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|主索引鍵|  
||傳輸類型|Min Occurs: 1<br /><br /> Max Occurs: 1|下拉式清單|以繫結檔案中指定的值來覆寫這個值。|  
||接收處理常式|Min Occurs: 1<br /><br /> Max Occurs: 1|下拉式清單|以繫結檔案中指定的值來覆寫這個值。|  
||管線|Min Occurs: 1<br /><br /> Max Occurs: 1|下拉式清單|以繫結檔案中指定的值來覆寫這個值。|  
||Description|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|以繫結檔案中指定的值來覆寫這個值。|  
||排程開始日期和排程停止日期核取方塊和下拉式清單方塊。|Min Occurs: 1<br /><br /> Max Occurs: 1|核取方塊和下拉式清單方塊。|以繫結檔案中指定的值來覆寫這些值。 即使未選取核取方塊值，仍然會匯入日期值。|  
||啟用服務窗口核取方塊|Min Occurs: 1<br /><br /> Max Occurs: 1|核取方塊|以繫結檔案中指定的值來覆寫這個值。|  
||服務窗口開始時間和服務窗口停止時間|Min Occurs: 1<br /><br /> Max Occurs: 1|捲動方塊|以繫結檔案中指定的值來覆寫這些值。 只有在 [啟用服務窗口] 值已設定時才有效。|  
|**結構描述**|Description|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|以繫結檔案中指定的值來覆寫這個值。|  
||追蹤 - 永遠追蹤所有屬性|Min Occurs: 1<br /><br /> Max Occurs: 1|核取方塊|以繫結檔案中指定的值來覆寫這個值。|  
||追蹤 - 選取所有訊息屬性|Min Occurs: 1<br /><br /> Max Occurs: 1|核取方塊|以繫結檔案中指定的值來覆寫這個值。 如果選取此值，也會啟用所有可以核取的訊息屬性。|  
||追蹤 - 個別屬性|Min Occurs: 0<br /><br /> Max Occurs: *|核取方塊|以繫結檔案中為此結構描述指定的追蹤屬性清單，覆寫該結構描述現有的追蹤屬性清單。<br /><br /> 如果匯入的繫結檔案會參考現有結構描述無法使用的追蹤屬性，便會產生錯誤。|  
|**對應**|Description|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|以繫結檔案中指定的值來覆寫這個值。|  
|**管線**|Description|Min Occurs: 1<br /><br /> Max Occurs: 1|文字方塊|以繫結檔案中指定的值來覆寫這個值。|  
||追蹤事件|Min Occurs: 1<br /><br /> Max Occurs: 1<br /><br /> (每個核取方塊)|核取方塊|以繫結檔案中指定的值來覆寫這些值。|  
||追蹤訊息內文|Min Occurs: 1<br /><br /> Max Occurs: 1<br /><br /> (每個核取方塊)|核取方塊|以繫結檔案中指定的值來覆寫這些值。|  
|**原則**|不適用。 原則不能匯出至繫結檔案。|不適用|不適用|不適用|  
|**角色連結**|不適用。 角色連結不能匯出至繫結檔案。|不適用|不適用|不適用|  
  
## <a name="unbinding-behavior-when-updating-existing-artifacts-with-matching-artifacts-in-a-binding-file"></a>以繫結檔案中的相符成品更新現有成品時的解除繫結行為  
 繫結檔案成品通常是設定成參考到其他成品，例如，我們通常將接收埠設定成參考接收位置。 在此例中，接收埠是父成品，而接收位置則是子成品。 接收埠是**明確**設定為參考接收位置和接收位置然後**隱含**參考接收埠。 如果在繫結檔案中有未完整設定的父成品 (例如，未以接收位置來設定的接收埠)，則不論這些成品在現有組態中的狀態如何，在匯入繫結檔案之後，它們的設定也將是不完整的。 比方說，如果您有現有的接收埠 myRP 與接收位置 myrl 設定和相同的接收埠 myrp 並繫結檔案中的是**不**設定接收位置 myrl 設定的則會採用的繫結檔案項目優先順序。 這個範例接收埠 myrp 並不會設定與接收位置之後匯入繫結檔案，因此您必須有效地**未繫結**myRL 從 myRP。  
  
 這個規則只適用於匯入明確設定參考的成品，而匯入具有隱含參考的成品則不適用。 因此，如果您匯入隱含參考 10 個其他成品的對應，而這些成品明確參考此對應，就不需要擔心對應會從隱含參考的成品解除繫結。  
  
## <a name="see-also"></a>另請參閱  
 [自訂繫結檔案](../core/customizing-binding-files.md)