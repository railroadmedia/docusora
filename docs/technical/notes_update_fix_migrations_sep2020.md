# Notes from attempting to update and fix migrations, September 2020

Jonathan M, September 2020

* [migrations error details, drumeo](#migrations-error-details--drumeo)
  + [note (2020-09-22)](#note--2020-09-22-)
  + [errors (2020-09-04)](#errors--2020-09-04-)
* [fixing some package migrations](#fixing-some-package-migrations)
  + [ecommerce](#ecommerce)
    - [One](#one)
    - [Two](#two)
    - [Three](#three)
  + [railcontent](#railcontent)
    - [One](#one-1)
    - [Two](#two-1)
  + [railnotification](#railnotification)
* [Problematic files on drumeo](#problematic-files-on-drumeo)

<!-- ecotrust-canada.github.io/markdown-toc -->

## migrations error details, drumeo

### note (2020-09-22)

I don't remember if each was addressed in a similar way. Sometimes you can fix the migration so it works—sometimes the "down" method just wasn't tested when the migration was created, and there might be a syntax or method-use error—other times I might have just deleted the migration file, but if that's the case, then that might explain subsequent errors.

Jonathan, Sept 22nd 2020

### errors (2020-09-04)

Run migrate:rollback for drumeo and you get these at each step…

1. migration not found
    1. 2019_10_03_128492_extend_ip_location_columns_in_linked_tables
    1. 2019_10_03_118432_extend_ip_location_columns_in_requests_table
    1. 2019_09_30_102300_create_media_tracking_tables
    1. 2019_08_01_145219_create_request_association_tables
1. (latter two are in the migrate_data_from_legacy_tables_Jan2020 branch railtracker branch)
1. 2019_07_05_142021_add_web_order_line_item_id_column_to_orders_table.php migration
    1. `SQLSTATE[42000]: Syntax error or access violation: 1091 Can't DROP 'web_order_line_item_id'; check that column/key exists (SQL: alter table `orders` drop `web_order_line_item_id`)`
1. 2019_07_05_075013_add_gateway_column_to_orders_table
    1. `SQLSTATE[42000]: Syntax error or access violation: 1091 Can't DROP 'gateway'; check that column/key exists (SQL: alter table `orders` drop `gateway`)`
1. Migration not found (not found an any remaining railtracker code)
    1. Migration not found: 2019_07_03_731791_increase_geoip_region_column_size
    1. Migration not found: 2019_06_27_978273_make_media_length_nullable
    1. Migration not found: 2019_06_26_945687_fix_wrong_unique_indexes
    1. Migration not found: 2019_06_26_133770_add_geoip_columns
    1. Migration not found: 2019_06_06_927433_add_generated_hash_columns
    1. Migration not found: 2018_10_24_946812_make_exception_message_column_long_text (found in *master* railcontent branch)
1. Migration not found: (both found in *master* railcontent branch)
    1. 2018_04_02_823024_add_indexes_to_media_playback_sessions_table
    1. 2018_04_02_823023_add_index_to_url_queries_table
1. might all have been in railtracker
    1. Migration not found: 2017_06_13_823022_create_media_playback_sessions_table
    1. Migration not found: 2017_06_13_823021_create_media_playback_types_table
    1. Migration not found: 2017_06_13_823016_create_request_exceptions_table
    1. Migration not found: 2017_06_13_823015_create_exceptions_table
    1. Migration not found: 2017_06_13_823014_create_response_status_codes_table
    1. Migration not found: 2017_06_13_823013_create_responses_table
    1. Migration not found: 2017_06_08_823012_create_requests_table
    1. Migration not found: 2017_06_08_823011_create_request_languages_table
    1. Migration not found: 2017_06_08_823010_create_geoip_table
    1. Migration not found: 2017_06_08_823009_create_request_devices_table
    1. Migration not found: 2017_06_08_823008_create_request_agents_table
    1. Migration not found: 2017_06_08_823007_create_request_methods_table
    1. Migration not found: 2017_06_08_823006_create_routes_table
    1. Migration not found: 2017_06_08_823005_create_urls_table
    1. Migration not found: 2017_06_08_823004_create_url_queries_table
    1. Migration not found: 2017_06_08_823003_create_url_paths_table
    1. Migration not found: 2017_06_08_823002_create_url_domains_table
    1. Migration not found: 2017_06_08_823001_create_url_protocols_table
1. 2017_04_07_171428_move_members_wordpress_tables_to_laravel_db
1. 2017_02_14_212005_add_stock_count_to_products_table
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `products` drop `stock_count`)`
1. 2017_02_01_203826_add_guarantee_to_products_table
    1. SIMILAR TO (BUT NOT EXACTLY THE SAME AS) `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `products` drop `stock_count`)`
    1. 2017_01_24_175801_change_users_birthday_column_to_date
    1. `SQLSTATE[22004]: Null value not allowed: 1138 Invalid use of NULL value (SQL: ALTER TABLE users CHANGE birthday birthday VARCHAR(255) NOT NULL;)`
1. 2016_08_31_203536_add_external_customer_id_to_credit_cards
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `credit_cards` drop `external_customer_id`)`
1. 2016_08_31_001635_make_subscription_payment_method_nullable
    1. `SQLSTATE[22004]: Null value not allowed: 1138 Invalid use of NULL value (SQL: ALTER TABLE subscriptions CHANGE payment_method_id payment_method_id INT(11) NOT NULL;)`
1. 2016_08_25_022625_add_first_last_name_to_address_table
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `addresses` drop `first_name`)`
1. 2016_02_03_182457_AddBadgesColumnToTeacherTable
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `teachers` drop `badges`)`
1. 2016_02_02_190501_AddCityRegionCountryColumnsToTeachers
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `teachers` drop `city`)`
1. 2016_01_26_220824_AddTeacherTimePerCostColumn
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `teachers` drop `teachingRateLessonLength`)`
1. 2016_01_25_210738_AddTeacherSpecialtiesToTeacherRow
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `teachers` drop `specialties`)`
1. 2016_01_15_185316_carousel_frame_change_event_date_to_event_sub_title
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: ALTER TABLE members_area_carousel_frames CHANGE event_sub_title event_date VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_unicode_ci null DEFAULT null)`
1. 2016_01_08_212942_change_carousel_eventDate_from_datetime_to_string
    1. `SQLSTATE[42S22]: Column not found: 1054 Unknown column 'event_date' in 'members_area_carousel_frames' (SQL: ALTER TABLE members_area_carousel_frames CHANGE event_date event_date DATETIME NULL DEFAULT NULL;)`
1. 2016_01_07_190400_carousel_change_position_from_string_to_int
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: ALTER TABLE members_area_carousel_frames CHANGE position position VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_unicode_ci NULL DEFAULT NULL;)`
1. 2015_12_18_174006_ConvertEventsTableContentIdToString
    1. `SQLSTATE[01000]: Warning: 1265 Data truncated for column 'content_id' at row 1 (SQL: ALTER TABLE members_area_events CHANGE content_id content_id INT(11) NULL DEFAULT NULL;)`
1. 2016_01_15_185841_ConvertDiscountAmountToFloat
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: ALTER TABLE railcenter_order_discounts CHANGE amount_subtracted amount_subtracted INT(11) NOT NULL;)`
1. 2015_11_12_181622_AddProductRenewingProductSkuToRenewalHistoryTable
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `railcenter_renewal_history_inf_ppal` drop `product_renewing_sku`)`
1. 2015_11_12_180010_AddProductRenewingIdToRenewalHistoryTable
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `railcenter_renewal_history_inf_ppal` drop `product_renewing_id`)`
1. 2015_11_05_212434_MakeInfPpalSubMapInfIdNullable
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: ALTER TABLE railcenter_inf_ppal_sub_map CHANGE inf_user_subscription_id inf_user_subscription_id VARCHAR(255) NOT NULL;)`
1. 2015_11_05_192117_AddInfAffiliateIdToOrderInfTable
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `railcenter_order_inf_data` drop `inf_affiliate_id`)`
1. 2015_10_30_152949_AddOrderItemIdToDiscountTable
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `railcenter_order_discounts` drop `order_item_id`)`
1. 2015_09_22_153221_addJobIdToOrderInfData
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `railcenter_order_inf_data` drop `inf_job_id`)`
1. 2015_09_18_180906_makeRailcenterProductSkuNotNullable
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: ALTER TABLE railcenter_products CHANGE sku sku VARCHAR(255) NULL;)`
1. 2015_09_16_175257_addUpSellOrderIdToOrdersTable
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `railcenter_orders` drop `originating_order_id`)`
1. 2015_09_16_160908_addInfTagsAndEmailIdsToOrderInfData
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `railcenter_order_inf_data` drop `applied_tag_ids`)`
1. 2015_08_27_203724_changeSomeProductTableColumnNames
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: ALTER TABLE railcenter_products CHANGE infusionsoft_product_id product_id INT)`
1. 2015_07_28_223523_productsTableSubscriptionIdNowUnique
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: ALTER TABLE railcenter_products DROP INDEX subscription_id)`
1. 2015_05_13_212648_add_teacher_welcome_video_col
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `teachers` drop `welcome_video`)`
1. 2015_05_13_184616_add_teacher_achievemnet_col
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `teachers` drop `achievements`)`
1. 2015_05_13_184550_remove_teacher_experience_col
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `teachers` add `experienceCredits` varchar(255) not null)`
1. 2015_04_22_183807_removeTeachingSinceMonthColumn
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `teachers` add `teachingSinceMonth` varchar(255) not null)`
1. 2015_04_16_202254_changeTeachingRateToInt
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: ALTER TABLE teachers MODIFY COLUMN teachingRate VARCHAR(255))`
1. 2015_03_26_220748_addForeignKeysDeleteCascade
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `teachers` drop foreign key `teachers_userid_foreign`)`
1. 2015_03_17_160257_changeTeacherLevelsTaughtToText
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: ALTER TABLE teachers MODIFY COLUMN levelsTaught VARCHAR(255))`
1. 2015_03_16_165134_changeTeachersExperienceColToText
    1. `SQLSTATE[42S22]: Column not found: 1054 Unknown column 'experienceCredits' in 'teachers' (SQL: ALTER TABLE teachers MODIFY COLUMN experienceCredits VARCHAR(255))`
1. 2015_03_11_175209_AddIsAcceptingStudentsColumnToTeachers
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `teachers` drop `isAcceptingNewStudents`)`
1. 2015_03_10_184708_AddCanBeContactedColumnTeachers
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `teachers` drop `canBeContacted`)`
1. 2015_03_03_231758_create_teacher_specialties
    1. `SQLSTATE[42000]: Syntax error or access violation: 1067 Invalid default value for 'created_at' (SQL: alter table `teacher_specialties` add `specialtyName` varchar(255) not null)`
1. Migration not found: 2015_01_27_162340_progress_remove_ip
1. Migration not found: 2015_01_20_232404_create_progress_action_table

<!-- --------------------------------------------------------------------------------------------------- -->

## fixing some package migrations

### ecommerce

as of [commit 94e4b7fd57641199cd8cb7d94cf78482339e101a ("We no longer want to just update all users subscriptions for any new payment method.", branch "2.4-")](https://github.com/railroadmedia/ecommerce/commit/94e4b7fd57641199cd8cb7d94cf78482339e101a)

#### One

migrations/2019_03_25_093475_make_sku_unique_product_table.php

needs (in "down" method)

`$table->dropUnique('sku');`

replaced with

`$table->dropUnique(['sku']);`

#### Two

migrations/2019_05_02_085255_update_stripe_customer_id_column_user_stripe_customer_ids_table.php

needs

```
public function down()
    {
        Schema::table('ecommerce_user_stripe_customer_ids', function (Blueprint $table) {
            $table->integer('stripe_customer_id')->change();
        });
    }
```

replaced with

```
public function down()
    {
        // https://github.com/doctrine/dbal/issues/3714 (note, is *Laravel* issue, not DBAL)
        DB::statement("ALTER TABLE ecommerce_user_stripe_customer_ids CHANGE stripe_customer_id stripe_customer_id INT");
    }
```

#### Three 

migrations/2020_07_28_847732_change_action_reason_to_string_membership_actions_table.php

needs

```
    public function down()
    {
        Schema::table('ecommerce_membership_actions', function (Blueprint $table) {
            $table->dateTime('action_reason')->nullable()->change();
        });
    }
```

replaced with

```
    public function down()
    {
        // https://github.com/doctrine/dbal/issues/3714 (note, is *Laravel* issue, not DBAL)
        DB::statement("ALTER TABLE ecommerce_membership_actions CHANGE action_reason action_reason DATETIME NULL");
    }
```

### railcontent

as of [commit cc93d747d521783ae9799fc13732a1acbe481b7c ("Now triggering crud content events after response is sent.", branch "0.5-")](https://github.com/railroadmedia/railcontent/commit/cc93d747d521783ae9799fc13732a1acbe481b7c)

#### One 

migrations/2018_04_30_185531_add_updated_on_index_to_user_content_progress_table.php

needs (in "down" method)

`$table->dropIndex('updated_on');`

replaced with:                

`$table->dropIndex(['updated_on']);`

#### Two

migrations/2020_02_12_073149_add_stats_epoch_to_content_statistics_table.php

needs (is "down" method)

`ConfigService::$tableContent,`

replaced with

`ConfigService::$tableContentStatistics,`


### railnotification

as of [commit 45a0aba849072844df25225020bbe4e7fc5c96ec ("Fixing indexes"\*, branch "master")](https://github.com/railroadmedia/railnotifications/commit/45a0aba849072844df25225020bbe4e7fc5c96ec)

(\*unrelated)

only one file here needs modification:

migrations/2020_01_13_19388_add_main_indexes_table.php

needs

```
    public function down()
    {
        Schema::table(
            'notifications',
            function (Blueprint $table) {
                $table->dropIndex('subject_id');
                $table->dropIndex('recipient_id');
                $table->dropIndex('read_on');
                $table->dropIndex('created_on');
                $table->dropIndex('type');
                $table->dropIndex('created_at');
                $table->dropIndex('updated_at');
            }
        );

        Schema::table(
            'notification_broadcasts',
            function (Blueprint $table) {
                $table->dropIndex('channel');
                $table->dropIndex('type');
                $table->dropIndex('status');
                $table->dropIndex('notification_id');
                $table->dropIndex('aggregation_group_id');
                $table->dropIndex('broadcast_on');
                $table->dropIndex('created_at');
                $table->dropIndex('updated_at');
            }
        );
    }
```

replaced with

```
    public function down()
    {
        Schema::table(
            'notifications',
            function (Blueprint $table) {
                $table->dropIndex(['subject_id']);
                $table->dropIndex(['recipient_id']);
                $table->dropIndex(['read_on']);
                $table->dropIndex(['created_on']);
                $table->dropIndex(['type']);
                $table->dropIndex(['created_at']);
                $table->dropIndex(['updated_at']);
            }
        );

        Schema::table(
            'notification_broadcasts',
            function (Blueprint $table) {
                $table->dropIndex(['channel']);
                $table->dropIndex(['type']);
                $table->dropIndex(['status']);
                $table->dropIndex(['notification_id']);
                $table->dropIndex(['aggregation_group_id']);
                $table->dropIndex(['broadcast_on']);
                $table->dropIndex(['created_at']);
                $table->dropIndex(['updated_at']);
            }
        );
    }
```

<!-- -------------------------------------------------------------------------------------------------- -->

## Problematic files on drumeo

These are files that by deleting (and their references in DB's migrations table) I could make migrate:reset (down all) work run without error. But, then if you to run migrate (up) it most likely wouldn't create the DB in the same state as before because a bunch of stuff wouldn't happen.

But, anyways, here's the list in case it's useful or interesting:

* '2015_03_03_231758_create_teacher_specialties',
* '2015_03_10_184708_AddCanBeContactedColumnTeachers',
* '2015_03_11_175209_AddIsAcceptingStudentsColumnToTeachers',
* '2015_03_16_165134_changeTeachersExperienceColToText',
* '2015_03_17_160257_changeTeacherLevelsTaughtToText',
* '2015_03_26_220748_addForeignKeysDeleteCascade',
* '2015_04_16_202254_changeTeachingRateToInt',
* '2015_04_22_183807_removeTeachingSinceMonthColumn',
* '2015_05_13_184550_remove_teacher_experience_col',
* '2015_05_13_184616_add_teacher_achievemnet_col',
* '2015_05_13_212648_add_teacher_welcome_video_col',
* '2015_07_28_223523_productsTableSubscriptionIdNowUnique',
* '2015_08_27_203724_changeSomeProductTableColumnNames',
* '2015_09_16_160908_addInfTagsAndEmailIdsToOrderInfData',
* '2015_09_16_175257_addUpSellOrderIdToOrdersTable',
* '2015_09_18_180906_makeRailcenterProductSkuNotNullable',
* '2015_09_22_153221_addJobIdToOrderInfData',
* '2015_10_30_152949_AddOrderItemIdToDiscountTable',
* '2015_11_05_192117_AddInfAffiliateIdToOrderInfTable',
* '2015_11_05_212434_MakeInfPpalSubMapInfIdNullable',
* '2015_11_12_180010_AddProductRenewingIdToRenewalHistoryTable',
* '2015_11_12_181622_AddProductRenewingProductSkuToRenewalHistoryTable',
* '2015_12_18_174006_ConvertEventsTableContentIdToString',
* '2016_01_07_190400_carousel_change_position_from_string_to_int',
* '2016_01_08_212942_change_carousel_eventDate_from_datetime_to_string',
* '2016_01_15_185316_carousel_frame_change_event_date_to_event_sub_title',
* '2016_01_15_185841_ConvertDiscountAmountToFloat',
* '2016_01_25_210738_AddTeacherSpecialtiesToTeacherRow',
* '2016_01_26_220824_AddTeacherTimePerCostColumn',
* '2016_02_02_190501_AddCityRegionCountryColumnsToTeachers',
* '2016_02_03_182457_AddBadgesColumnToTeacherTable',
* '2016_08_25_022625_add_first_last_name_to_address_table',
* '2016_08_31_001635_make_subscription_payment_method_nullable',
* '2016_08_31_203536_add_external_customer_id_to_credit_cards',
* '2017_01_24_175801_change_users_birthday_column_to_date',
* '2017_02_01_203826_add_guarantee_to_products_table',
* '2017_02_14_212005_add_stock_count_to_products_table',
* '2019_07_05_075013_add_gateway_column_to_orders_table',
* '2019_07_05_142021_add_web_order_line_item_id_column_to_orders_table',

<!-- --------------------------------------------------------------------------------------- -->
